---
layout: post
author: <a href="/about">Hung-Chi Cheng (程弘錡)</a>
categories: iOS
tags:  Firebase
date:  2017-10-26
last_modified_at: 2018-07-17
title: "Note for iOS Firebase Push Notification/ Cloud Message (FCM)"
---
<!--                Title 的建議最大長度                   -->

* content
{:toc}

<!-- 文章概要 -->
<div class="video-container">
<center><iframe width="100%" height="315" src="https://www.youtube.com/embed/sioEY4tWmLI" frameborder="0" allowfullscreen></iframe></center>
</div>
>Firebase Cloud Messaging (FCM) is a cross-platform messaging solution that lets you reliably deliver messages at no cost. Using FCM, you can notify a client app that new email or other data is available to sync. You can send notification messages to drive user reengagement and retention. For use cases such as instant messaging, a message can transfer a payload of up to 4KB to a client app.

<!-- more -->
Firebase Cloud Message : <https://firebase.google.com/docs/cloud-messaging/>


<!-- 著作權start -->
<center><b><br>
一一一一一一一一一一一一一一一一一一一一一一一一<br>
&copy; Hung-Chi's Blog<br>
<a href="https://hungchicheng.github.io/2017/10/26/Note-for-iOS-Firebase-Push-Notification-Cloud-Message-FCM/" id="link" target="_blank">
	https://hungchicheng.github.io/2017/09/29/Note-for-iOS-Firebase-Push-Notification-Cloud-Message-FCM/
</a><br>
一一一一一一一一一一一一一一一一一一一一一一一一
</b></center>
<!-- 著作權end -->

<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## How to Implementing Push Notifications on iOS with Firebase
>Push Notifications is a loud and powerful way for our apps to engage with our users. We engage with our users by letting them see values with their very owns eyes. Users see values. Users engage. We can engage our users by letting them know about something important. Perhaps their favorite sport team is about to compete. A flash sale on watermelons is on for 30 minutes. Or there is an important meet up in the desert later this weekend. These are some scenarios when our users may want to be notified.

Here Steps : <https://www.appcoda.com/firebase-push-notifications/>

## My Code in iOS

```objc

    // Firebase sdk 2017/10/16
    // [START configure_firebase]
    [FIRApp configure];
    // [END configure_firebase]
    
    // [START set_messaging_delegate]
    [FIRMessaging messaging].delegate = self;
    // [END set_messaging_delegate]
    
    // Register for remote notifications. This shows a permission dialog on first run, to
    // show the dialog at a more appropriate time move this registration accordingly.
    if (floor(NSFoundationVersionNumber) <= NSFoundationVersionNumber_iOS_7_1) {
        // iOS 7.1 or earlier. Disable the deprecation warnings.
#pragma clang diagnostic push
#pragma clang diagnostic ignored "-Wdeprecated-declarations"
        UIRemoteNotificationType allNotificationTypes =
        (UIRemoteNotificationTypeSound |
         UIRemoteNotificationTypeAlert |
         UIRemoteNotificationTypeBadge);
        [application registerForRemoteNotificationTypes:allNotificationTypes];
#pragma clang diagnostic pop
    } else {
        // iOS 8 or later
        // [START register_for_notifications]
        if (floor(NSFoundationVersionNumber) <= NSFoundationVersionNumber_iOS_9_x_Max) {
            UIUserNotificationType allNotificationTypes =
            (UIUserNotificationTypeSound | UIUserNotificationTypeAlert | UIUserNotificationTypeBadge);
            UIUserNotificationSettings *settings =
            [UIUserNotificationSettings settingsForTypes:allNotificationTypes categories:nil];
            [[UIApplication sharedApplication] registerUserNotificationSettings:settings];
        } else {
            // iOS 10 or later
#if defined(__IPHONE_10_0) && __IPHONE_OS_VERSION_MAX_ALLOWED >= __IPHONE_10_0
            // For iOS 10 display notification (sent via APNS)
            [UNUserNotificationCenter currentNotificationCenter].delegate = self;
            UNAuthorizationOptions authOptions =
            UNAuthorizationOptionAlert
            | UNAuthorizationOptionSound
            | UNAuthorizationOptionBadge;
            [[UNUserNotificationCenter currentNotificationCenter] requestAuthorizationWithOptions:authOptions completionHandler:^(BOOL granted, NSError * _Nullable error) {
            }];
#endif
        }
        [[UIApplication sharedApplication] registerForRemoteNotifications];
        // [END register_for_notifications]
    }

```
[Firebase : Github Sample](https://github.com/firebase/quickstart-ios/tree/master/messaging/MessagingExample)<br>
<!-- 手動放廣告 -->
{% include ad-in-post.html %}
<!-- 手動放廣告 -->

## Reference
[Firebase Cloud Message]<br><https://firebase.google.com/docs/cloud-messaging/><br>
[appcoda guild]<br><https://www.appcoda.com/firebase-push-notifications/><br>
[iOS quick sample]<br><https://github.com/firebase/quickstart-ios/tree/master/messaging/MessagingExample><br>
[Problems to receive]<br><https://github.com/firebase/quickstart-ios/issues/345><br>
[Firebase Status]<br><https://status.firebase.google.com/><br>
