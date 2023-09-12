---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: Vue3
tags:  Vue3 vue3-google-login GoogleIdentityServices
date:  2023-09-01
last_modified_at: 2023-09-12
title: "Vue3 Login with Google Identity Services in 2023"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->
In the fast-evolving landscape of web application development, user authentication plays a pivotal role. One of the most widely adopted methods for user authentication is Google Login. However, as of 2023, there have been significant changes in the way Google Login is implemented and integrated into web applications. This introduction will provide an overview of the latest practices and challenges associated with integrating Google Login into your Vue.js application.
<!-- more -->


<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy; Hung-Chi's Blog<br>
<a href="https://hungchicheng.github.io/2023/09/01/Vue3-Login-with-Google-Identity-Services-in-2023/" id="link" target="_blank">
	https://hungchicheng.github.io/2017/12/07/Vue3-Login-with-Google-Identity-Services-in-2023/
</a><br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- 著作權end -->

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->


## The Google Login Package

- [vue3-google-login](https://www.npmjs.com/package/vue3-google-login)

To facilitate Google Login integration in Vue.js applications, we recommend using the `vue3-google-login` package, version 2.0.18. This package supports the latest Google Identity authentication method, providing users with a secure and seamless login experience.

As part of the integration process, you'll need to manage essential elements such as clientId, uri configurations, and testing accounts within the Google Cloud Console. This is where you can create and configure the necessary credentials for your application. For those who are new to this process or need a refresher, we'll guide you through the steps to obtain your Google API Client ID.

## Obtaining Google API Client ID

1. Start by accessing the [Google API Console](https://console.cloud.google.com/apis) and navigate to the "Credentials" page.
2. Create a new Google API project or select an existing one. If you have previously set up the "Use Google Account for login" feature or Google One Tap, you can use the existing project and web client ID. Keep in mind that when developing a production application, you might require multiple projects, each repeating the subsequent steps.
3. Click on "Create credentials" and select "OAuth client ID." Under "Application type," choose "Web application" to create a new client ID. If you already have a client ID, select one of the existing "Web application" options.
4. Ensure you add your website's URI to the list of authorized JavaScript origins. The URI should include only the necessary configurations and the complete hostname.
   For example:

   ```
   https://www.example.com
   http://localhost
   http://localhost:5173
   ```

5. Make sure to record the obtained Client ID for later use in your Vue.js application.

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## Installing and Using the Package

To integrate Google Login into your Vue.js application, you'll need to follow these steps:

1. Install the `vue3-google-login` package.

```javascript
import { createApp } from 'vue'
import App from './App.vue'
import vue3GoogleLogin from 'vue3-google-login'

const app = createApp(App)

app.use(vue3GoogleLogin, {
  clientId: 'YOUR_GOOGLE_CLIENT_ID (obtained in the previous step)'
})

app.mount('#app')
```

2. Utilize the package within your Vue.js components.

```vue
<script setup>
const callback = (response) => {
  // This callback will be triggered when the user selects or logs in to
  // their Google account from the popup
  console.log("Handle the response", response)
}
</script>

<template>
  <GoogleLogin :callback="callback"/>
</template>
```

For more in-depth guidance and advanced features, please refer to the [package documentation](https://devbaji.github.io/vue3-google-login/).

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->


## Considerations for Integration
> Warning: The support of Google Sign-In JavaScript platform library for Web is set to be deprecated after March 31, 2023. The solutions in this guide are based on this library and therefore also deprecated.Use instead the new Google Identity Services for Web solution to quickly and easily sign users into your app using their Google accounts.By default, new client IDs are now blocked from using the older platform library; existing client IDs are unaffected. New client IDs created before July 29th, 2022 may set the plugin_name to enable use of the legacy Google platform library.

For more information, please see Deprecation and Sunset page.

We've listed some of the Vue.js integration packages that are currently unsupported due to these changes:

- [vue-authenticate: v1.5.0](https://www.npmjs.com/package/vue-authenticate) - Lacks TypeScript support and relies on an outdated API.
- [vue-authenticate-2: v2.1.0](https://www.npmjs.com/package/vue-authenticate-2) - An extension with TypeScript support, but still using the outdated API.
- [@websanova/vue-auth: v4.2.1](https://www.npmjs.com/package/@websanova/vue-auth) - Fully supports Vue and TypeScript but is not compatible with the new Google Identity Services.
- [vue-auth3: v1.0.10](https://www.npmjs.com/package/vue-auth3) - A Vue 3 and Axios version of the above, with the same outdated API.

As a result, these packages are currently unusable, and we may need to wait for updates to make them compatible again.

## An Alternative Solution: Firebase

For those seeking a robust alternative, consider using [Firebase](https://firebase.google.com/). Firebase provides seamless integration with various social platforms, including Google, Facebook, Twitter, and more. With Firebase, you can obtain tokens and connect to your server, benefiting from its extensive backend capabilities.

Firebase offers a free quota that includes 50,000 daily reads, 20,000 daily writes, and 20,000 daily deletes. It is highly recommended and offers a comprehensive solution for social platform integration and backend functionalities. While powerful, the decision to use Firebase may depend on your specific project requirements and preferences.