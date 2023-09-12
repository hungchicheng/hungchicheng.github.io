---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: Passport
tags:  Passport Express JWT
date:  2023-09-12
last_modified_at: 2023-09-12
title: "Passport and JWT Authentication in Express"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->


There are many applications of Passport on the internet. In this article, we will briefly explain the process of using Passport for identity authentication and token validation.

Passport is a module used with Express specifically for handling identity authentication. Its principle is to use middleware to independently handle "authentication" as a functionality. It has modules for various third-party authentication providers like Facebook, Google, Twitter, etc.

Built on top of express.js, we'll implement token-based authentication using `passport-local` and `passport-jwt`.
<!-- more -->


<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy; Hung-Chi's Blog<br>
<a href="https://hungchicheng.github.io/2023/09/12/2023-09-12-Passport-and-JWT-Authentication-in-Express/" id="link" target="_blank">
	https://hungchicheng.github.io/2023/09/12/2023-09-12-Passport-and-JWT-Authentication-in-Express/
</a><br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- 著作權end -->

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->



## Packages

We are using the following packages for this:

- `jsonwebtoken` for JWT functionality
- `bcrypt` for encryption
- `passport`, `passport-local`, `passport-jwt` for related authentication

## Preparing the User Model

Assuming a simplified User model, containing id, account, and encrypted password:

```ts
const users = [
  {
    _id: 1,
    account: 'user01',
    // '1234' encrypted by bcrypt
    password: '$2b$10$Kmz54B8hEgDVy0uy3j6qucBLYFa3PFNHo6lU1rub4RPyD89qaMi'
  },
  {
    _id: 2,
    account: 'user02',
    // '5678' encrypted by bcrypt
    password: '$2b$10$DSsxhvpOi8nPwajJFCKTuT663yAtwMVLagYdTLWmAP.LGxPOEB2C'
  }
]
```

The password is encrypted using bcrypt, which is a one-way hash algorithm. For example, '$2b$10$Kmz54B8hEgDVy0uy3j6qucBLYFa3PFNHo6lU1rub4RPyD89qaMi' is the result of encrypting '1234' with bcrypt, generated using:

```ts
bcrypt.hash('1234', 10)
```

The User model provides two methods: findById and findOne, which are used to look up user objects by id and account, respectively.

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## Introduction to Passport

Passport abstracts identity authentication into "authentication strategies." Well-defined authentication strategies are hooked into a global object using `passport.use`, and then the `passport.authenticate` middleware assigns the authentication strategy to be used. Therefore, concerning identity authentication, you only need to use the Passport module specific to your strategy.

In this article, we use `passport-local` and `passport-jwt` for account-password login and JWT authentication, respectively.

- passport-local: Local authentication or registration of account/password and token issuance

```ts
passport.use(
  // Specify the authentication strategy name as 'UserLogin,' which corresponds to the route configuration
  'UserLogin',
  // Use passport-local strategy here
  new LocalStrategy(
    { usernameField: 'account' },
    // Local verification function, equivalent to User Model's user.findOne({ account });
    (username, password, done) => {
      return verifyLocalFunc(User, username, password, done);
    }
  ),
);
```

## Token Validation Mechanism

The first step is to generate a token for the frontend after successful login using `jsonwebtoken`. Here's how you can do it:

- jsonwebtoken: Generate a JWT token

```ts
const token = jwt.sign({ id: user.id }, process.env.JWT_SECRET!);
```

Token validation is similar to passport-local, so you can create a strategy accordingly.

- passport-jwt: Validate whether the token is legitimate and send it

```ts
passport.use(
  // Specify the authentication strategy name as 'UserJwt,' which corresponds to the route configuration
  'UserJwt',
  // JWT authentication
  new passportJwt.Strategy(
    JWT_STRATEGY_OPTIONS,
    // Retrieve the id from the jwtToken and use user.findById(userId) to look up the user object
    (jwtToken, done) => {
      return verifyJwtCB(User, jwtToken.id, done);
    }
  ),
);
```

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## Route Configuration

Finally, combine it with routes:

- login: Perform identity authentication to obtain a token. After successful validation, it enters the middleware login, which issues the token.
- logout: Use logout to demonstrate JWT authentication. Other requests may also require this. Here, we validate whether a legitimate token is present. Passport is compatible with Express, and the mechanism is similar to inserting authentication middleware into routing, allowing the next function to execute after successful validation.

```ts
// Call passport.authenticate() and specify the authentication strategy as UserLogin, which uses passport-local strategy
router.post('/login', passport.authenticate('UserLogin'), userController.loginSuccess);

// Call passport.authenticate() and specify the authentication strategy as UserJwt, which uses passport-jwt strategy
router.post('/logout', passport.authenticate('UserJwt', { session: false }), userController.logout);
```

## Completing Passport's Login and Logout Serialization

The `serializeUser` function is used to convert a user object into an id, and `deserializeUser` is used to convert an id into a user object. This allows you to access the user object in `req.user`.

```ts
passport.serializeUser((user, done) => {
  done(null, user.id);
});

passport.deserializeUser(async (id, done) => {
  try {
    const user = await User.findById(id);
    if (user) done(undefined, user);
  } catch (err) {
    done(err);
  }
});
```

## Testing

You can use Postman to log in and get a token, and then use the token to log out to test the entire process.

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->


With the configurations described above, you can achieve login/logout/JWT authentication.