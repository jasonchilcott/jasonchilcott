---
layout: page
title:  "It’s About Time"
date:   2021-10-22 12:30:00 -0400
categories: blog
---

![image](/assets/img/Tanaka-Hisashige-Myriad-Year-Clock-3.jpg)


## *I am currently job hunting. Please see my [resume](/resume/resume) and [get in touch](mailto:jasonchilcode@gmail.com)*
## *This post was originally made when I was a Software Engineering student at Flatiron School*

I’m writing this blog now. Or am I? When is now? I’m not just asking these questions because I have been awake for almost thirty hours straight. Well, in a way I am, because the past few days (a day consists of 86,400,000 milliseconds,) I have been thinking a lot about dates and time. And datetime.
My partner and I decided to build a web app that could be used to make reservations at a restaurant. As we were planning out our models, one of the most obvious attributes we would need for a reservation is the “When.” I chose to represent this important piece of data as one discreet unit, :datetime, rather than separate columns in the table for time and date each.
However, on the front-end, humans don’t think of time just as a series of digits. History, memories, seasons, different times of the day or night. Friday evening versus Monday morning. A person making a reservation wouldn’t pick time and date like it is one single object. So we used separate pickers for time and date.
The JSX looked like this

![image](/assets/img/time-1.png)

But then it had to be joined to `datetime`

![image](/assets/img/time-2.png)

So it could look like this to go to the back-end

![image](/assets/img/time-3.png)

But when that information came back to the front-end, it looked like this

![image](/assets/img/time-4.png)

At first we thought to `.split(‘T’)` and use `.slice(0,-8)` to get rid of the bit on the end, but found a better way by doing this

![image](/assets/img/time-5.png)

But then I noticed our reservation times looked strange. The romantic dinner I had planned was now scheduled for 2PM!
Thankfully we only planned on demoing our app in New York, so I could easily just do this to make sure when the datetime went into the database it did so with the offset specified by ISO-8601.

![image](/assets/img/time-6.png)

Around the same time, we decided to make the default value for the date picker to be the current day, which looked like this.

![image](/assets/img/time-7.png)

All in all, between Javascript, HTML and Ruby, it’s a lot of time spent, thinking about time.

So what’s going on?

If you paid attention to my last blog, you know that Brendan Eich basically had 864,000,000 milliseconds (that’s 10 days) to write the first version of Javascript for Netscape. Date and time are very complex, and Javascript borrowed its date handling from the very trendy, but still very young, Java. While 25 years have passed and Javascript has evolved in so many ways, it still has its quirks, and date is one of the wildest.

A Javascript date is specified as the number of milliseconds since midnight UTC on January 1st, 1970. If you’re curious how many milliseconds it’s been since then, type `new Date().getTime()` into a Javascript console. One year is 31,536,000,000 milliseconds. Not as catchy as that song from Rent. Although it has a base in UTC, all the methods work in the local time zone. The user’s local time zone and UTC are the only zones natively supported.

While in real life, the universe is probably billions of years old (or a computer simulation,) for Javascript, the earliest date is 100 million days before January 1st, 1970 UTC. That’s April 20, 271,821BCE. 100 million days in the other direction, time ends for Javascript on September 13th, 275,760CE.

![image](/assets/img/time-8.png)
*That’s 273,660 years after the Second Impact.*

Date has over 50 instance and static methods in Javascript, but they aren’t necessarily human friendly. The differences between browsers and time zones can make parsing risky, as I can tell you from experience. The set/get methods for minutes and make sense, minutes and seconds start at zero. If you use 24-hour time, hours starting at zero is comfortable. But the setMonth/getMonth methods represent February with 1 and December with 11. Makes sense from a computer point of view, but it can lead to easy confusion when you aren’t sure exactly what you are looking at. Thankfully, yet paradoxically, setDate/getDate start at 1 as the first date of the month.

Unlike Ruby, which has a plethora of formatting options for date and time, if you’re trying to get Javascript to be more multisyllabic than “Thu” or “Nov,” you’re going to have to get DIY with objects and functions. I’m not even going to get started on ordinals.

The relationship between humans and the information tools we use to process the world around us fascinates me. And the way the community finds and addresses issues inspires me. Moment.js is such an example. Brendan Eich himself, along with Maggie Johnson-Pint and Matt Johnson are with TC-39 are spearheading the proposal for Temporal to address more of the issues with Javascript and date handling.

It’s about time.


### Further Reading:

[Date on MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

[Fixing JavaScript Date – Getting Started](https://maggiepint.com/2017/04/09/fixing-javascript-date-getting-started/)

[Temporal TC39 Proposal](https://tc39.es/proposal-temporal/docs/index.html)

[Understanding Date and Time in JavaScript](https://www.digitalocean.com/community/tutorials/understanding-date-and-time-in-javascript)

[Ruby strftime](https://apidock.com/ruby/DateTime/strftime)

[Moment.js](https://momentjs.com/)
