# What is the maximum amount of data that can be stored in localstorage,and what are the implications of this limit for web applications?

LocalStorage is a data storage type of web storage. This allows the JavaScript sites and apps to store and access the data without any expiration date. 
 According to the HTML5 spec,Local Storage has 10MB per webapplication this limit can be increased by the user when needed; 
however, only a few browsers support this.

One Local Storage per web application, with a max size of 10MB, is available for a given browser and is shared by all windows and tabs of that browser. 

If you run a app in multiple tabs and windows, they all share the same LocalStorage data , subject to a max limit of 5MB. 
If you were to then open that same application in another browser, say FireFox, then the new browser would get its own Local Storage to share with all its own tabs and windows. 
![Alt text](LocalStorage.png)


# How does session storage differ from localstorage, and in what scenarios would you want to use one over the other
sessionStorage is similar to localStorage; the difference is that while data in localStorage doesn't expire, data in sessionStorage is cleared when the page session ends.

* Whenever a document is loaded in a particular tab in the browser, a unique page session gets created and assigned to that particular tab. That page session is valid only for that particular tab.
* A page session lasts as long as the tab or the browser is open, and survives over page reloads and restores.
* Opening a page in a new tab or window creates a new session with the value of the top-level browsing context, which differs from how session cookies work.
* Opening multiple tabs/windows with the same URL creates sessionStorage for each tab/window.
* Duplicating a tab copies the tab's sessionStorage into the new tab.
Closing a tab/window ends the session and clears objects in sessionStorage
![Alt text](localVsSession.png)

# Is there a maximum limit to the amount of data that can be stored in sessionstorage, and if so,how might this impact webapplication development

Session storage maximum  size is limited by only by system memory.

When data is added to, modified, or removed from LocalStorage or SessionStorage, a StorageEvent is fired within the current browser tab or window. That Storage event contains the storage object in which the event occurred, the URL of the document to which this storage applies, and both the old and the new values of the key that was changed. Any listener registered for this event can handle it.

**Note: **Although the HTML5 spec calls for Storage events to be fired in all tabs of the same browser or all windows of the same browser, few browsers currently implement this.

# How does the use of cookies impact the performance of webapplications,and what are some potential security concerns associated with cookies?

The term “cookie” refers to just the textual information about a website. In order to recognize you and show you results according to your preferences, this website saves some information in your local system when you visit a particular website. The history of the internet has long been marked by the use of cookies. A website visitor asks the server for a web page when they visit it. Every request for a server is unique. Likewise, if you visit a hundred times, each request will be considered unique by the server. Since a server receives many requests every second, storing every user’s information on a server doesn’t seem logical and obvious. The same information may not be needed again if you don’t return. Therefore, a cookie is sent and stored on your local machine to uniquely identify you. You will receive a response from the same server the next time you hit it since it recognizes you. Almost every server uses this cookie (some exceptions exist today because of advertisements). Therefore, although you might have many cookies in your system, such cookies will be recognized by a server and analyzed.

When cookies were first developed, they were used to better the developer’s experience. Consider visiting a website in a language other than your native one (let’s say English). You can select English as your language from the website’s language section. It might be necessary to switch languages five times a day if you visit the same website five times. These details are therefore stored in a cookie on your system. This ensures that the server knows that you wish to view the website in English the next time you send a request. Cookies are vital in this regard. The scale cookies used today are much smaller than the example above.

* The storage capacity of Cookies is 4KB
* Cookies expire based on the setting and working per tab and window 
* Both clients and servers can read and write the cookies
* Data transfer to the server is exist
* It is supported by all the browser including older browser

# What happens to the data stored in local storage when the browser is closed,and how might this impact user experience in web applications?

LocalStorage is a data storage type of web storage. This allows the JavaScript sites and apps to store and access the data without any expiration date. This means that the data will always be persisted and will not expire. So, data stored in the browser will be available even after closing the browser window.

In short, all we can say is that the localStorage holds the data with no expiry date, which is available to the user even after closing the browser window. It is useful in various ways, such as remembering the shopping cart data or user login on any website.

In the past days, cookies were the only option to remember this type of temporary and local information, but now we have localStorage as well. Local storage comes with a higher storage limit than cookies . It also does not get sent with every HTTP request. So, it is a better choice now for client-side storage. Some essential points of localStorage need to be noted:

* localStorage is not secure to store sensitive data and can be accessed using any code. So, it is quite insecure.
* It is an advantage of localStorage over cookies that it can store more data than cookies. You can store 5MB data on the browser using localStorage.
* localStorage stores the information only on browser instead in database. Thereby the localStorage is not a substitute for a server-based database.
* localStorage is synchronous, which means that each operation executes one after another.

# What are some common use cases for cookies,and how might they be used to improve user experience in web applications

Cookies are files, often including unique identifiers, that are sent by web servers to web browsers, and which may then be sent back to the server each time the browser requests a page from the server.

Cookies can be used by web servers to identity and track users as they navigate different pages on a website, and to identify users returning to a website. Cookies may be either "persistent" cookies or "session" cookies. A persistent cookie consists of a text file sent by a web server to a web browser, which will be stored by the browser and will remain valid until its set expiry date (unless deleted by the user before the expiry date). A session cookie, on the other hand, will expire at the end of the user session, when the web browser is closed.

Cookies are used to 
* to recognize your computer when you visit the website
 to track you as you navigate the website, and to enable the use of any e-commerce facilities
* to improve the website's usability
* to analyze the use of the website
* in the administration of the website
* to personalize the website for you, including targeting advertisements which may be of particular interest to you.

* Session management. For example, cookies let websites recognize users and recall their individual login information and preferences, such as sports news versus politics.
* Personalization. Customized advertising is the main way cookies are used to personalize your sessions. You may view certain items or parts of a site, and cookies use this data to help build targeted ads that you might enjoy.
* Tracking. Shopping sites use cookies to track items users previously viewed, allowing the sites to suggest other goods they might like and keep items in shopping carts while they continue shopping.

# If you want to improve the performance of a web application on the client-side,what storage mechanism would you recommend using,and why?

## indexedDB
IndexedDB is a non-relational database. It is good for storing all kinds of data, like: JS objects, files, blobs, etc. It works asynchronously through transactions and is based on events.

Use IndexedDB to store structured data. This includes data that needs to be searchable or combinable in a NoSQL-like manner, or other data such as user-specific data that doesn’t necessarily match a URL request. Note that IndexedDB isn’t designed for full-text search.

## Cache Storage API
CacheStorage API is a powerful tool. We can cache our static app resources, like HTML, CSS, and JavaScript. It allows us to ensure that they are always instantly available.

You can use the Cache Storage API to download, store, delete or update assets on the device. Then these assets can be served on the device without needing a network request.

Use the Cache Storage API for network resources, things you’d access by requesting them via a URL, such as HTML, CSS, JavaScript, images, videos, and audio.

* IndexedDB and CacheStorage are supported in every modern browser. They’re both asynchronous and will not block the main thread. They’re accessible from the window object, web workers and service workers.

* By using CacheStorage API and IndexedDB lets you effectively store all the resources that your app needs to run.

* For offline storage, use the Cache API.

* For storing application state and user-generated content, use IndexedDB.

# How do the security implications of local storage and session storage differ,and what steps can be taken to ensure that sensitive user data is properly secured?

LocalStorage as it’s called it’s local storage for your browsers, it can save up to 10MB. Client side reading only.

As developers, we should avoid using localStorage because it’s synchronous and cause performance issues. Also we should not store any security or sensitive data in it
Sensitive data includes: User IDs, Session IDs, JWTs, Personal information, Credit card information, API keys.

oes the same, but as it’s name saying, it’s session based and will be deleted after closing your browser, also can save less than LocalStorage, like up to 5MB. Client side reading only. Also we should not store security data in it.

# Under what circumstances can cookies be accessed by JavaScript running on a different domain than the one that set the cookie,and what steps can be taken to mitigate potential security risk sassociated with this behavior?

domain=site.com
A domain defines where the cookie is accessible. In practice though, there are limitations. We can’t set any domain.

There’s no way to let a cookie be accessible from another 2nd-level domain, so other.com will never receive a cookie set at site.com.

It’s a safety restriction, to allow us to store sensitive data in cookies that should be available only on one site.

By default, a cookie is accessible only at the domain that set it.

Please note, by default a cookie is also not shared to a subdomain as well, such as forum.site.com.

    // if we set a cookie at site.com website...
        document.cookie = "user=John"

    // ...we won't see it at forum.site.com
        alert(document.cookie); // no user

For historical reasons, domain=.site.com (with a dot before site.com) also works the same way, allowing access to the cookie from subdomains. That’s an old notation and should be used if we need to support very old browsers.

To summarize, the domain option allows to make a cookie accessible at subdomains.


.
