---
layout: post
title: "Learning Vue - Intro to Vue3"
date: 2023-04-09 17:45:00 +0000
categories: web
---

I have been wanting to learn backend development for a while using Java. I have played around with different frameworks like Django, but I seem to be drawn to using Java, hence why I started learning Spring. But this writeup is not about Java Spring. As a backend engineer. It will be great to have some frontend skills, and being familiar with HTML and CSS, there was no other option but to go with Vue since it's much more closely tied to HTML. Vue is a Javascript framework for building user interfaces, and if you're familiar with HTML and CSS, I think it should feel at home for you. With a little knowledge of Javascript, getting started should be a breeze for you.

## Some History

After a long childish grudge with Javascript, I have finally picked up a Javascript framework for building apps. I remember my first experience with Javascript being quite frustrating; being a beginner and having lots of different opinions as to what to use, what to do, and what not, I got fed up and jumped ship into mobile development. As a beginner in my early programming years, all I wanted was to learn programming, not find myself in cyber arguments with each side saying their framework and conversions are the best. I found the mobile development community to be very linear, and you quickly know what to learn, The learning curve may be steep, but there is a clear layout as to what to do.




## Let's goo Vue

Back to Vue: Getting started with Vue is much easier than I thought. Just following the documentation on the Vue website quickly helped me setup Vue and run the initial demo project that comes after configuring your Vue project. Vue programming is built around having different units of UI called components. Let's consider these components as a system that is capable of accepting some inputs called props and sending signals to the environment using events (emitting events). Vue is based on something called component-based programming, and understanding how to fit together components and how they communicate helps you build user interfaces.

I'm still in my first week of learning Vue, and I'm pretty much catching the concepts easily. With Vue built around having components, let me walk you through some sample code to appreciate Vue.


## Setting up your environment

Vue can be setup by using a package from npm called create-vue. This seems to be the default way of doing it, but you can also run Vue without using these "build-tools". You can simply import a script to the Vue CDN. Let's go with the former. In order to set up a Vue project with npm, you need to have npm installed on your system. After installing npm, you can simply setup the project using ```npm init vue@latest```. This will spawn up the latest Vue package, ```create-vue``` and run the project creation wizard.

The wizard presents you with some options, from which you must choose yes or no. If you're completely new to Vue or front-end development, go with no for each option. Follow any further instructions to run Vue on a local server that come with project wizard.

## Vue components

Vue components are written in "Single-File Component (SFC)" format; this term just describes how you layout your component code. Your component code is separated into ```template```, ```script```, and ```style``` sections. To create a Vue component, create a new file and name it with a ```.vue``` extension. Your html code goes into the template section; the script section contains javascript code for rendering html code based on some state or data; and finally, the style section contains styling code.

sample code

{% highlight liquid %}
    {% raw %}
// filename: Hello.vue

<script>
    export default {
        data() {
            return {
                text: 'Hello, World'
            }
        }
    }
</script>

<template>
    // {{ code }} allows interaction with Javascript expressions
    <p> {{ text }} </p>
</template>

<style>
    p {
        font-weight: bold;
        font-size: 32px;
        color: green;
    }
</style>

{% endraw %}
{% endhighlight %}

Vue components can be developed either using the ```Options``` API or the ```Composition API```. These two just define how you describe the component's logic. With the Options API, you have an object of options such as data, computed, and methods. The Composition API defines your component's logic using import API functions. The Composition API is seen as being much more concise and letting you do more with less code. But both options are capable, and whoever you choose will be based largely on your preferences. The Options API seems to be more beginner-friendly, and people coming from an OOP background will be able to easily adopt it. The Composition API seems to be tied more to a reactive style of programming.

Sample code for comparison

{% highlight liquid %}
    {% raw %}
// Options API
<script>
    export default {
        data() {
            return {
                text: 'Hello'
            }
        }
    }   
</script>

<template>
    <h1>{{ text }}</h1>
</template>

    {% endraw %}
{% endhighlight %}

{% highlight liquid %}
    {% raw %}
// Composition API
<script>
    import { ref } from 'vue'
    // store text value in a reactive state
    const text = ref('Hello')
</script>

<template>
    <h1>{{ text }}</h1>
</template>

    {% endraw %}
{% endhighlight %}

These sample codes above describe what's known as declarative rendering, which is a core Vue feature where, using template syntax extending HTML, we describe how the HTML should look based on Javascript state, and when the state changes, HTML automatically updates itself.

## Let's end here

Vue declarative and component-based styles of building user interfaces should be easy to pick up for anybody wanting a framework with a low learning curve and low barrier of entry. As I keep on learning Vue, I will dive into more Vue features and document everything I have been learning here. So far, I have been liking the experience, and I really intend on gaining some vue skills.