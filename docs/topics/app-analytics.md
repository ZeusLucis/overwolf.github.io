---
id: app-analytics
title: Using Analytics in your App
sidebar_label:  Integrating App Analytics
---

One of the most effective ways to improve your app and learn more about your users is implementing solid analytics that provide you with usage statistics. Stats support your product decision making by providing real-world user usage data, including showing how users actually interact with each part of your product. Analytics also underline where users drop off and lose interest, what product abilities are completely ignored and much more.

We recommend using a web analytics service to collect app data, measure user engagement and improve monetization. Our preference is the industry standard [Google Analytics](https://marketingplatform.google.com/about/analytics/features/).

Please take the time you need to implement any chosen analytics service thoroughly and test it to make sure it's working as intended.

## Google Analytics: Basic Implementation

### Update your manifest.json

Open up the external connections necessary for communicating with the Google service:

```json
{
"data":{  
   "externally_connectable":{  
      "matches":[  
         "https://*.google-analytics.com",
         "http://www.google-analytics.com"
      ]
   }
}
```

### Create a Google Analytics account and generate a new property

Select "Website" as your tracked object, enter your website name, website URL and select your preferred reporting time zone.

<div class="box" data-slick='{"slidesToShow": 1}'>
  <a data-fancybox="gallery" data-caption="Create a new property" href="../assets/app-analytics/GA1.jpg">
     Create a new property
    <span class="thumb">
      <img src="../assets/app-analytics/GA1.jpg" alt="process">
    </span>
  </a>
</div>

### Update your pages

Let's assume that you want to track events in your index page. In your /index.html, add a reference to the tracking script in a separate file:

```html
<!DOCTYPE html>
<html>
<head>
  ...
  <script src="js/index.js"></script>
  ...
</head>
<body>
  ...
</body>
</html>
```

### Update your tracking code

Add the tracking JavaScript, for example at js/index.js, with the Universal Analytics code. Note the “https” at the start of the script address.

```js
// Standard Google Universal Analytics code
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function()
   {
      (i[r].q=i[r].q||[]).push(arguments)
   },
   i[r].l=1*new Date();a=s.createElement(o),
   m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
   // Note: https protocol here
})(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

ga('create', 'UA-XXXXX-YY', 'auto');

// Removes failing protocol check. @see: http://stackoverflow.com/a/22152353/1958200
ga('set', 'checkProtocolTask', function(){}); 
ga('require', 'displayfeatures');
ga('send', 'pageview', '/index.html');
```

If that all went well, you should see page tracking appear in Google Analytics, like so:

<img src="https://overwolf.github.io/docs//assets/app-analytics/GA-sample.jpg" alt="process" width="900"/>


## More info

Find more information on best practices and more guides for implementing google analytics [here.](https://analytics.google.com/analytics/academy/)
