# Attacking the cult: Clean Code

----------

## Intro

-   This is what I think about the ideology of Robert Martin. This is just an opinion. I'm not Robert Martin and I don't want you to blindly follow it or stop asking questions. Keep sharp, be skeptical.

-   When I say "you do not need" - it literally means you do not need it. If it's called a best practice, but you can't define any actual reason why it's good - you do not need it. Think for yourself, don't be afraid to question dogmas. Curiosity, including critical curiosity, is the key to self-development. There are no axioms in this life. Every point is a theorem.

----------

## The mindset I want to promote

### 1. No matter how confident the talker is, always ask: “Who’s saying?”, “What’s the proof?”, “Why should I believe you?”, “What’s your profit?” I won’t agree with anything but directly related facts. Cut to the chase. I don’t care about marketing: you can keep talking, then I will ask for facts. Emotions, feelings, experience, titles - are not related facts.

### 2. Be "Oh wow, everyone understood - great, but I still have questions" one. Don't be shy.

Lastly, remember your high school. How many critically thinking classmates you had? See? It's always the same ratio.

---
## Some of those principles _do_ help maintainability when used with common sense.

Yes, but, he has not invented them.

**Robert Martin didn’t invent SOLID. He popularized and packaged pre-existing ideas.**  
The SOLID principles were coined by Michael Feathers based on earlier work from Barbara Liskov, Bertrand Meyer, and others. Martin just bundled them into a convenient acronym and added his opinionated takes around them.

----------

# Part 1: Misleading

1.  The irrelevance of the outdated Java-specific concepts is mind-blowing.

2.  It was written in 2008, when there were no web frameworks, and requests were directly going to IP addresses bound to static HTML files.

3.  Yet, somehow most developers take the shitposts of Martin as the "Bible of OOP."
    -   Object-oriented programming is a great concept. And it has nothing to do with Robert Martin.
    -   Martin also pulled a great marketing move and publicly claimed the expression “clean code.”
        - Now, whenever you mean actually clean code and say those two words, people understand it as slow, infinitely-abstracted shitcode. Whereas you just meant: code covered with tests and documentation.
3.  It's important to not mix different fields of development. Quick rule: if you're gonna use creational patterns - yes, you need abstractions. Otherwise - no.

    -   For example, in game dev you need a lot of objects, probably in the front-end as well, I don't know. However, in scripting, inside actual business logic (not talking about CRUD tho) -  you do not need them. For what? Readability or "best practices?" or what other pointless reason? Maybe "Everyone does it" or "Clean Code says" ?

4.  These takes are about monolith code. In microservices, you do not need any abstraction.

    -   However, I’ve read posts by some abstraction-addicted individuals who try to implement SOLID in Go or C. This is mental. Google hasn't added OOP to increase the value of code. But anyway these geniuses are faster.

5.  You pay the price with performance.

6.  There’s no such thing as “clear code” and there never can be. Because you will never know what will be needed tomorrow. So you either decompose every component to dust, or don’t change it at all.

    -   Never think in “What if we will need one more of this?”

    -   Because what if you will not? Or what if you do, but it’s the part that was not abstracted?

    -   So what now, abstract every line of code to dust? Abstract every single bit?

    -   It's bullshit. You’ll need to write new code anyway.

    -   Another classic example: You have a class that prints documents. One day you get a document in Arabic, or you need to print on a specific printer where you also need to scan the colors of the document and provide them as RGB in JSON format. And these sorts of problems I can list endlessly. The fact that you’ve made a separate class for printing doesn’t solve anything. You still need to write new code for a specific use case.

7.  The takes of Martin are nothing but ephemeral concepts. That’s not a room, that’s a field for misinterpretation.

    -   Have you ever seen any “Microservices teacher”? But you definitely have seen “SOLID teachers” who say, “Pay me and I will explain the meaning of those sacral words.”

    -   Moreover, I can write a function with a dozen responsibilities and then prove to you the responsibility is single. Try to guess why.

8.  Whatever Martin suggests is not engineering. Engineering should not care about interpretation of concepts (Easter egg style). Every single person should understand exactly the same thing when they hear a principle. It should not depend on intent, mood, or experience. Engineering is not about feelings.




----------

# Part 2: Arrogance

This year, in 2025, I finally listened to _Clean Code_ and _Clean Architecture_ after 13 years (I couldn't find the book in university years, then I was lazy).

And the arrogance of the author was breathtaking - a masterclass in gatekeeping from someone who speaks as if he invented programming and you, “a damn junior,” breathe his air. You understand?!

However, the quote **“Reckless developers should be punished”** was the last drop of my patience.  
Einstein, Hawking, Armstrong... none of them could ever let themselves speak this way.  
Who the fuck do you think you are? In your entire life, you’ve written only a no-name testing framework. Are you sure you’re the one who can act like this?

Like, I worked with developers - guys who finished one and a half online courses and know everything, except for the phrase “I don’t know / I’m not sure.” But Martin has polished it into a brand.

So I went looking for his engineering legacy.

----------

# Part 3: The legacy of Robert Martin

And the “best ever programmer” has:

-   **FitNesse (2002)** - An unremarkable Java testing tool, ***which lacks the SOLID overengineering he preaches.*** When it comes to real coding, the guru doesn’t follow his own principles. ***qham***  
    By the way, this tool “just works,” and it’s not high-performance.

-   **Datalog (1980s)** - A C++ inference engine. No visible impact today. “Used everywhere in medical and financial systems,” as Robert Martin says. (No public proof. “Believe me bro.”)

-   **Clean Code Examples (2008)** - Awesome.  
    And he did consulting work (1980s–2000s). Wow.


To be honest, I was expecting a background and legacy richer than Guido van Rossum or Linus Torvalds.  
Martin gave us… uhm... PowerPoint slides about SOLID.

The lesson is clear: those who _do_ rarely lecture, and those who _lecture_ often haven’t done much. Yet somehow, we accept “STFU and listen to me” from architects whose biggest project is a testing framework?

That said, the archetype of the developer who never says “I don’t know” (but should), is always wrong (but never learns), and is painfully loud (but empty) - has a role model.

----------

## Analogy

Microservices are not God's gift. However, microservices:

-   Don’t have any ephemeral bullshit that anyone can interpret however they want. Strict recommendations, no marketing or pseudo-intellectualism. → Clarity.

-   Solve the problem of future scaling for real. Not in the “Clean Code” way - where you preemptively abstract something and hope _that_ will be needed (but not another thing). So, even if you don’t want to scale your app, you lose nothing. Take the same piece of code and extend it anytime you want without touching it.


Someone argued with me recently and said, “Microservices are also not needed in most cases” - in the context of “All approaches have strengths and weaknesses” (like monolith vs microservices).  
The point here is the scaling problem - which microservices actually solve. And if you don’t overengineer (which would be misuse), you’re guaranteed to have a scalable app.  
Whereas “Clean Code” doesn’t guarantee anything.

--- 
## The cult

Most importantly, this book became cult, literally because the some developers are incompetent.
- They pay for SOLID coaches or other outsiders who could not find a job, to teach them what "LSP" means.
- Like any shitpost on LinkedIn, under posts filled with disgusting conceptual mistakes. Published by someone just like him - to pretend to be "competent," and one day one HR to send them a JD.

And whenever you will question their base, they will surrender, not because they blindly believe, because **if they agree to you, that means they need to learn something new, which they don't want.**  That's why, you are wrong. You are threatening their competency.

- And for HRs, do you really buy this shitshow? Just open their portfolio, copy the project name and try to find on YouTube. Simple.

----------
## P.S.

-   “I’ve never actually read the book, but Clean Code sounds important so you must be wrong.”
-   “People say it’s the industry standard, so who are you to criticize?”
-   “This is disrespectful. Martin is a legend and made software better for everyone.”
-   “You just don’t get the point of Clean Code. It’s not about abstraction for abstraction’s sake.”
-   “SOLID principles are universal. You’re being reckless advocating for code without structure.”
-   “You’re undermining team discipline. Without principles, junior devs write garbage.”
-   “You think you’re being practical, but this mindset causes long-term tech debt.”
-   “Abstractions protect us from chaos.”


---
## P.P.S.

- “Clarity” means everyone understands it - not just people who’ve read a $50 book. ;)
