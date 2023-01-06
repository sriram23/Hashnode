# What are Core Web Vitals?

Web Vitals are the speed metrics used for measuring the user experience on web pages. **Core Web Vitals** are the subsets of the Web Vitals, which are focused on measuring the following aspects:

* Loading
    
* Interactivity
    
* Visual stability
    

The Core Web Vitals are not only for better user experience but also for SEO. As of 2021, Google considers it as one of the ranking factors. A good Core Web Vital score would give a boost to the site in ranking.

## Metrics

As of 2023, we have 3 Core Web Vital metrics. The metrics would continue to evolve. You may see some metrics would get added in future. The following are the Core Web Vital metrics:

* LCP - Largest Contentful Paint
    
* FID - First Input Delay
    
* CLS - Cumulative Layout Shift
    

### LCP

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672934266367/fbb7c9df-fbf6-4178-9b0b-022afa6225ca.png align="center")

LCP is the measure of time taken to load the largest image or text block in the visible viewport.

*Example:* The time taken for the largest image to load in the viewport.

The optimum threshold for LCP would be:

* 0 - 2.5s -&gt; Good
    
* 2.5s - 4s -&gt; Needs Improvement
    
* \&gt;4s -&gt; Poor
    

### FID

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672934586312/3ae83806-350e-4041-a1dd-03e5123550b2.png align="center")

FID is the measure of time taken between the user interacting with the controls on the page to the browser starting processing the event for the control.

*Example:* Time between the user typing in a textbox and the onChange event called in the browser.

The optimum threshold for FID would be:

* 0 - 100ms -&gt; Good
    
* 100ms - 300ms -&gt; Needs Improvement
    
* \&gt;300ms -&gt; Poor
    

### CLS

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672934998781/4bd53352-6adb-4535-876d-e6a9ebf9fe70.png align="center")

CLS is the measure of unexpected layout shifts throughout the lifecycle of the page.

*Example*: When a user is trying to interact with the page and the page shifts due to the introduction of some additional components (like alerts, ads), resulting in triggering some other action, which the user is not intended for.

The optimum threshold for CLS would be:

* 0 - 0.1 -&gt; Good
    
* 0.1 - 0.25 -&gt; Needs Improvement
    
* \&gt;0.25 -&gt; Poor
    

## How to measure Core Web Vital Metrics?

The following are the way, in which we can measure the Core Web Vital Metrics.

### 1\. Google Search Console

In the [Google Search Console](https://search.google.com/search-console/core-web-vitals?), we have a menu called Core Web Vitals, in which we can measure the metrics based on the last 90 days' data of the webpage. This is possible only if you are the owner of the website. Google would verify your ownership of the website, before letting you check the details of the website.

### 2\. Page Speed Insight

[Page Speed Insight](https://pagespeed.web.dev/) is a tool, in which we can measure the metrics just by typing the URL for websites.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672935963434/4d371798-be46-4c4c-a357-a07fac4c0a56.png align="center")

### 3\. Lighthouse

Lighthouse is a tool that comes with the chrome dev tools in chrome browsers. We can use this tool to analyse the page load.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672936288569/ebeb4757-782a-497b-8e31-0febb270f404.png align="center")

### 4\. Chrome Dev Tools

We can use the Performance tab in the Chrome dev tools as well to measure the metrics, just by checking the *Web Vitals* checkbox.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672936083284/fcb962f7-b9a9-4e55-b2ea-4d9e04dc8a08.png align="center")

### 5\. Web Vital Chrome Extension

We can use the [Web Vital Chrome Extension](https://chrome.google.com/webstore/detail/web-vitals/ahfhijdlegdabablpippeagghigmibma?hl=en) (Addon) to measure the metrics. We can measure just by navigating to the website in the browser. The extension would provide the metric details.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672936718418/c7594e0b-f5d1-4fe2-bb99-ed34cba5e0a0.png align="center")

That's all about the Core Web Vitals. Hope this is useful to you. Looking forward to your suggestions and feedback. Thank you!