Cordova AccountKit Plugin
======
The Apache Cordova wrapper around the Facebook [AccountKit](https://www.accountkit.com/).

## Installation

1. Create Facebook Developer Account
2. Get a Facebook App ID  (`APP_ID`)
3. Get an AccountKit client token (`CLIENT_TOKEN`)
4. To install the plugin in your app, execute the following (replace variables where necessary):

```bash
cordova plugin add cordova-plugin-accountkit --save \
   --variable APP_ID="123456789" \
   --variable APP_NAME="myApplication" \
   --variable CLIENT_TOKEN="abcdefghijklmnopqrstuvwxyz"
```

If you need to change your `APP_ID` after installation, it's recommended that you remove and then re-add the plugin as above. Note that changes to the `APP_ID` value in your `config.xml` file will *not* be propagated to the individual platform builds.

### Android

It is recommended to add these permission to `config.xml` of your Cordova project to reduce the friction during the login process ([more info](https://developers.facebook.com/docs/accountkit/android/configuration)):
```xml
<uses-permission android:name="android.permission.RECEIVE_SMS" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
```

## API

### Login

`AccountKitPlugin.loginWithEmail(Function success, Function failure)`
`AccountKitPlugin.loginWithPhoneNumber(Function success, Function failure)`

Success function returns an Object like:

	{
		accountId: "<string>",
		applicationId: "<string>",
		token: "<long string>",
		lastRefresh: 1451606400,
		refreshInterval: 2592000
	}

Failure function returns an error String.

### Logout

`AccountKitPlugin.logout()`

### Get access token

`AccountKitPlugin.getAccessToken(Function success, Function failure)`

Success function returns an Object like:

	{
		accountId: "<string>",
		applicationId: "<string>",
		token: "<long string>",
		lastRefresh: 1451606400,
		refreshInterval: 2592000
	}
