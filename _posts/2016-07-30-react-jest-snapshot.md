---
title: React Tree Snapshot Testing
layout: post
---

I am really happy using [enzyme](http://airbnb.io/enzyme) for testing my React components. But, a couple of days ago [Facebook announced](https://facebook.github.io/jest/blog/2016/07/27/jest-14.html) a new feature on Jest: *Snapshot Testing*.

Snapshot testing is an alternate model to the typical way you would work when using Enzyme and working with the DOM. Instead, when using snapshot testing, you run Jest to create snapshots of your components and store them as text files. Every time you run Jest after that, the snapshots get compared and if they don't match the test fails. You get the option to accept the change or fix your components.

You can take multiple snapshots, for example: 
- take snapshot
- simulate a click
- take another snapshot

This is the output after a successful run:

![Success]({{ site.url }}/assets/jest-snapshot-success.png)


If we change something, for example introducing a typo, the test will fail:

![Fail]({{ site.url }}/assets/jest-snapshot-fail.png)


This is a great alternative when working with visual components, as it allows you to get up and running immediately with easy-to-write tests.


I've created a demo project, you can take a look at it [here](https://github.com/nicolasiugo/try-jest-snapshot).
It's really easy to set up:

1 - create package.json file that should look something like this:
{% highlight javascript %}
{
  "dependencies": {
    "classnames": "^2.2.5",
    "react": "15.2.0",
    "react-dom": "*"
  },
  "devDependencies": {
    "babel-jest": "*",
    "babel-preset-es2015": "*",
    "babel-preset-react": "*",
    "jest": "*"
  },
  "scripts": {
    "test": "jest"
  },
  "jest": {
    "automock": false,
    "testEnvironment": "node"
  }
}
{% endhighlight %}

2 - run npm install

3 - create file .babelrc:
{% highlight javascript %}
// .babelrc
{
  "presets": ["es2015", "react"]
}
{% endhighlight %}

4 - create a folder named __tests__

Tests files goes inside this folder. When you are done creating the test, just run 
{% highlight shell %}
npm test
{% endhighlight %}

