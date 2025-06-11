_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean Andreasian._

---
## Content
- [Stone Age](#stone-age)
- [1990s - Early 2000s: The PHP Era](#1990s---early-2000s-the-php-era)
- [Late 2000s](#late-2000s)
- [2010s](#2010s)


---
# Stone Age


Before having fancy web frameworks, the internet was working using “hosting a directory”.

> - What is “hosting a directory”?
> 
> - It’s when the directory is bound to IP:Port

Example:

```cmd
mkdir service
python3 http.server --bind 127.0.0.1 8080
```


#### This means any files in the folder are accessible with url.

- The `service/home.html` file is accessible via https://127.0.0.1:8080/home.html
- The `service/about.html` file is accessible via https://127.0.0.1:8080/about.html


---
# 1990s - Early 2000s: The PHP Era

In the 90’s PHP became a popular solution.

Remember: `http:www.facebook.com/home.php` ?

PHP was allowing to _*generate_ html files and return using templating. _(generate is exaggeration, as anything in programming)_


#### For example if the URL was: `http:www.facebook.com/home.php?user=John?lang=en`

#### Simply said in each `.php` file was one function, which may get arguments:

- #### It was getting the request
- #### Passing the arguments (`John` and `en`) into the HTML file using templating (HTML templating example: `jinja` in Python, `erb` in Ruby)
- #### It might pull data from a database and insert it into the page if it was needed, then pass thru templating


---
# Late 2000s

This was the time of:

- **Web Frameworks:** Django (2005), Ruby on Rails (2004), ASP.NET MVC. Helped build dynamic web apps quickly with routing, templating, DB handling


- **REST APIs / AJAX:** Frontends started making dynamic requests (jQuery, XHR), separating UI and data. JSON over HTTP became the norm

---
# 2010s

- **CDNs (Content Delivery Networks)** early 2010’s. Used to serve static assets (images, JS, CSS) faster worldwide


- **Responsive Design** early 2010’s. Media queries, mobile-first design. 


- **HTML5 & CSS3** early 2010’s. New standards added features like video/audio support, canvas, local storage, and advanced styling.


- **Single Page Applications (SPAs)** early to mid 2010’s. AngularJS, then React, then Vue. Frontend handled all rendering; backend became API-only.


- **Containers & Microservices** mid 2010s. Docker (2013), Kubernetes (2014). Monoliths got split into microservices, deployed as containers


- **Serverless / Functions-as-a-Service** late 2010s. AWS Lambda, Google Cloud Functions. Code runs without managing servers at all


- **Edge computing / Jamstack / Next.js-style Hybrid** late 2010s to early 2020s. CDN + serverless + dynamic rendering at the edge

---
