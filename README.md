# Checking Xfinity (Comcast) Data Usage

After overruning my data cap or coming very close almost every month, I decided to look at an automated way to keep me updated throughout the month. Comcast doesn't have a public API so I reverse engineered the website which allows you to see your current month's usage and previous four months.

Given that the API this library uses isn't public, there's no guarantee it will continue to work over time. Comcast will almost definitely make breaking changes to the API and this library will have to be updated when they do so.

I ended up building an entire Node.js application which uses this library as a local module and then dumps the results into MongoDB. At this time, I'm only planning to publish this library and not the whole application.

## Usage

---

I am using this library as a local module right now. The steps below will get you up and running with a simple Node.js application. This assumes this library is in the same parent folder as `test-app`

This library uses two environment variables for your Xfinity username and password. Be sure these variables are set

`XFIN_USERNAME`

`XFIN_PASSWORD`

## Create and run your own sample app

---

```sh
mkdir test-app
cd test-app
npm init -y #-y flag will accept all defaults

npm install --save <path to xfinity library>
```

## Then create `index.js` in the `test-app` folder

---

```javascript
//index.js
const checker = require('xfinity-library');
  

checker.retrieveDataFromXfinity().then((data) => {
    console.log(data);
})
.catch((err) => {
    console.log(err);
});
```

## Finally, run the app

---

_don't forget the environment variables_

```bash
XFIN_USERNAME=account@hotmail.com XFIN_PASSWORD=Password1 node .
```
