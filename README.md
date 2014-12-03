## DumpGetSatisfaction
---
This is a half day project, and it is an HTML page that easily dump all topics and replies from Get Satisfaction community with Javascript. The data is in JSON format and can be parsed and migrate to different platforms.

So if you want to export all data from Get Satisfaction and then import them into new system, this project should be helpful :-D

### The story behide
Get Satisfaction announces that they will stop offering free plan since December 3rd, 2014. The "Professional" plan listed on their website is 1,200 USD per month, which is quite expensive. As a company, the price may be affordable, but who are willing to pay so much for just a forum? Well, I can hear they start to say it is not just a forum. Of course it has some value-added services and tools, but still many people won't buy it.

We ([ForeUI](http://www.foreui.com/) team) used Get Satsifaction for several years, and now we decide to stop using Get Satisfaction. We contacted their customer service and wish they can export our data for us to be used in new system. We tried this first because we saw they claimed that they offer one-time export when user leave (see [their official claim](https://getsatisfaction.com/getsatisfaction/topics/need_to_export_all_topics_and_their_answers#reply_9904120)). However, they refused our request and said this export service "is for our paying clients as it takes a good amount of time for our developers". They suggest us to use the "Export" feature in the manage console, which is useless because it only exports the list of title. So we are on our own now.

It doesn't take long to make such a script to dump all data we need, and we belive it could be useful for others, so we put it on Github.

### The used APIs
This script uses only two APIs from the Get Satisfaction platform.

To get topics as JSON object:
https://api.getsatisfaction.com/companies/yourCompanyName/topics.json

To get replies for specific topic:
https://api.getsatisfaction.com/topics/topicId/replies.json

There is an interesting thing: the first API supports JSONP, while the second one doesn't :-)

So we use https://jsonp.nodejitsu.com/?url= as the JSONP proxy to get the data. It works very good and we are considering to integrate it into [ForeUI](http://www.foreui.com/), so the "Get JSON Object" action can always cross site, even the API doesn't support JSONP.

### Usage
Please open the "DumpGetSatisfaction.html" file in your text editing tool first, you will need to replace at least the "yourCompanyName" parameter.

By default the parameters are set to dump all available topics and replies. Depending on how much data you have, you may consider dumping the data part by part (to avoid crashing your web browser process at the end).

Then you load the "DumpGetSatisfaction.html" file in your web browser, and it will start to work by itself.

No worry if an error happens when getting an topic or reply, the script will keep retrying until the data is collected successfully.

Once it is done, it will take some time to prepare the data for you to download. If the data is huge, you'd better to copy the JSON data from the text area at the bottom and paste it to your text editor (and save to file).