# Tools-for-Instagram
Automation scripts for Instagram </br></br>
<img src="https://media.giphy.com/media/ignhVpXU7h4qHMwXix/giphy.gif" width="340">
## How to use it
    1. Rename .env_example to .env and edit the configuration.
    2. Execute main.js to test the scripts. 
## Bot skills:
- [x] Login Flow
- [x] Save Cookies in files
- [x] Remove Cookies
- [x] Get User Information
- [x] Get Followers of account (save into a txt file)
- [x] Like Content by URL
- [x] Like Content by MediaId 
- [x] Like Content by Post
- [x] Follow by Username
- [x] Follow User by Post
- [x] Unfollow by Username
- [x] Get recent posts list of a hashtag
- [x] Get top posts list of a hashtag
- [x] Get recent post list by location
- [x] Get top post list by location
- [x] Save post list into scrape list
- [x] Implement lowdb Database
- [x] Save Likes information
- [x] Save Follows information
- [x] Save Unfollows information
- [x] Get Like activity
- [x] Get Follow activity
- [x] Get Unfollow activity
- [x] Current Time In Range Validator [ex: from 8:00 to 23:00]
- [ ] Proxies
- [x] Multi-login
- [x] Like Recent Hashtags By Intervals
- [ ] Simple Bot
- [ ] Postprocessing of scrape list (detect faces, language, business accounts)
## Wiki

https://github.com/linkfy/Tools-for-Instagram/wiki

## Follow the project

You can follow the streams of the project on the Twitch channel<br>
https://www.twitch.tv/mimi_twitchbot

## Follow the development status

Follow the development status to see what's the next upcoming idea<br>
https://trello.com/b/ZlwRr6l0/tools-for-instagram


## Api mods

- Injected loggedInUser inside ig Object after login (ig.loggedInUser)
- Injected db inside ig Object after login (ig.db)
- Injected shortid generator inside ig Object

# Api
### Basic example
```javascript
require('./src/tools-for-instagram');

(async () => {
    let ig = await login();
    
    // .. Implement your code here
    let info = await getUserInfo(ig, "Instagram");
    console.log("User information, username: " + info.username);
    
    // ..

})();
```
#### loadConfig(loginFileName)
Load a config file from the logins folder
```javascript
    let acc = loadConfig('exampleAccount');
    let myAccount2 = await login(acc.account, acc.password);
    //same as await login("username", "password");

```
#### getUserInfo(ig, username)
Get the user information of the desired username
```javascript
   let info = await getUserInfo(ig, 'Instagram');
```
#### getFollowers(ig, username)
It will save the followers inside the outputfolder with the format "acountName_followers.json"
```javascript
   await getFollowers(ig, 'Instagram');
```
#### likeUrl(ig, username, [force: bool])
like the desired instagram Url, the like will be saved inside database. 
```javascript
   await likeUrl(ig, 'https://www.instagram.com/p/B1gzzVpA462/');
```
If 'force' is set to true, when the item was already liked before it will force to continue the operation.
```javascript
   await likeUrl(ig, 'https://www.instagram.com/p/B1gzzVpA462/', true);
```


#### isTimeInRange(startTime, endTime)
Returns True or False if the current time is inside the range
```javascript
   await isTimeInRange("10:00", "23:00");
```
It is also possible to calculate night ranges between the current day and tomorrow.

```javascript
   await isTimeInRange("23:00", "3:00");
```

#### likeRecentHashtagsByIntervals(ig, hashtagArray, intervals, likesPerInterval, waitMinutesBetweenLikes)

Automate like actions on given array of recent hashtags feed

```javascript
    let likesPerInterval = 15;
    let waitMinutesBetweenLikes = 3;

    let intervals = [
        ["7:00",    "8:00"],
        ["10:00",   "11:00"],
        ["22:00",   "23:00"],
    ];
    let hashtagArray = [
        "cats",
        "dogs",
        "music"
    ];

   let likeInterval = likeRecentHashtagsByIntervals(
                                                    ig,
                                                    hashtagArray, 
                                                    intervals, 
                                                    likesPerInterval,
                                                    waitMinutesBetweenLikes);
```
It is also possible to stop the interval clearing it

```javascript
   clearInterval(likeInterval);
```



### This documentation is not yet finished...
#### recentHashtagList()
#### topHashtagList()
#### likePost()
#### recentLocationList()
#### topLocationList()
#### savePosts()
#### followUser()
#### getLikeActivityByHours()
#### getFollowActivityByHours()
#### getUnfollowActivityByHours()
#### getLikeActivityFromHourToNow(ig, "12:00")
#### lastLikeMinutesAgo(ig)
#### removeCookie(ig)
#### followRecentHashtagsByIntervals(ig, hashtagArray, intervals, followsPerInterval, waitMinutesBetweenFollows)