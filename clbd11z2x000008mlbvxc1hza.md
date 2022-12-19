# How I used the RSS feeds to display my blogs on my website (Part 1)

Hello World!

Let me show you how I used the RSS feeds to display blogs on my website. But before that let us see what's RSS.

# What is RSS?

RSS (Really Simple Syndication) is nothing but a file, that contains a summary of updates from the websites in XML format. We can find the RSS feeds of the website with the [RSS icon](https://upload.wikimedia.org/wikipedia/en/thumb/4/43/Feed-icon.svg/128px-Feed-icon.svg.png).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1670376514792/bOlaMmB9z.png align="center")

An RSS feed would look like this:

![A sample RSS feed](https://cdn.hashnode.com/res/hashnode/image/upload/v1670376306875/ihN4vVBmD.png align="center")

RSS feed contains details like titles, descriptions, image links, etc. We can make use of the RSS feed viewers that are available online. Below is an RSS feed parsed with an RSS viewer online.

![RSS feed parsed with a RSS viewer online](https://cdn.hashnode.com/res/hashnode/image/upload/v1670376939390/SsZhzwtmA.png align="center")

# How I used RSS to get my blogs?

As we saw earlier, the RSS feed contains meta-data about the website like title, description and image link. I used an express server to convert the RSS feeds, which are in XML format to JSON format so that I can integrate them easily into my website.

## Steps to achieve:

1.  Create a simple express server.
    
2.  Fetch the RSS feed.
    
3.  Convert RSS feeds to JSON.
    

## Implementation

### A simple express server

First, let's create an express server where we will be fetching and parsing the RSS feeds.

```bash
yarn init -y
# or
npm init -y
```

Install the following dependencies:

*   Express
    
*   RSS Parser (rss-parser) - An npm package to convert RSS feeds to JSON.
    

```bash
yarn add express rss-parser
```

Let's create the `server.js` and run a basic server.

```javascript
const express = require('express');
const app = express();
app.get('/', (req, res) => {
  res.send('The server is running');
});
app.listen(4000, () => console.log('Server is running on localhost:4000'));
```

Type `node server` in the terminal, we could see the app start running in localhost:4000. When we open it in the browser, we could see the message `The server is running` printed.

### API to fetch blogs from RSS feeds

Now let's write an API to fetch the posts from RSS feeds. For that, we would be using the `rss-parser` npm package. We'll have to pass the feed URL to the rss-parser's `parseURL` function, which would return a JSON response. Below would be the code for it.

```javascript
// importing rss-parser
let Parser = require('rss-parser');
// creating an instance for the rss-parser
const parser = new Parser();

app.get('/fetch-blogs', async(req, res) => {
    // process.env.HASHNODE_FEEDS would be our RSS feed link
    parser.parseURL(process.env.HASHNODE_FEEDS).then(resp => {
    res.status(200).send(resp)
  }).catch(err => res.send(err))
})
```

The final code would be:

```javascript
const express = require('express');

let Parser = require('rss-parser');
const parser = new Parser();

const app = express();

app.get('/', (req, res) => {
  res.send('The server is running');
});

app.get('/fetch-blogs', async(req, res) => {
    parser.parseURL(process.env.HASHNODE_FEEDS).then(resp => {
    res.status(200).send(resp)
  }).catch(err => res.send(err))
})

app.listen(4000, () => console.log('Server is running on localhost:4000'));
```

Now we are done with writing the API, let's test it.

*   Run the server typing `node server` in the terminal.
    
*   Head over to the browser and hit `localhost:4000/fetch-blogs` in the URL bar.
    

We would be able to see the JSON response of our RSS feeds. Since this is a 'get' request, we can run and test this in the browser itself.

![JSON response form the server](https://cdn.hashnode.com/res/hashnode/image/upload/v1670379206681/pxJSezKBP.png align="center")

Now we can fetch the JSON response from the RSS feed. In the next post, I will be writing about how we can make use of this JSON to display our posts in a UI application (website). Stay tuned!

Hope this is helpful to you. Looking forward to your feedback. Thank you!