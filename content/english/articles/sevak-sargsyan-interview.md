---
title: "Sevak Sargsyan: \"If you want to be a competitive programmer, you need to study mathematics\""
date: 2023-01-12T15:24:40+04:00
categories:
  - interview
tags:
  - IT
summary: About software vulnerabilities that can become a cybersecurity problem and provoke hacker attacks, new trends in the IT industry, education in this area and much more, we talked with the head of the RAU System Programming Department Sevak Sargsyan.
---

![Sevak Sargsyan](/images/sevak-sargsyan-interview/main.webp)

**About software vulnerabilities that can become a cybersecurity problem and provoke hacker
attacks, new trends in the IT industry, education in this area and much more, we talked with the Head of the System
Programming Department of the Russian-Armenian University, a specialist in the field of compiler technologies and
analysis programs, Candidate of Physical and Mathematical Sciences Sevak Sargsyan.**

_- Name the most common security problems in software._

If you look at the history of attacks, then the main security problem in the software is the mistakes made by
programmers. These errors occur because people write the code. A simple example is a text: a student has written a
thesis, there are typos or some grammatical errors. The same is true with programming: the code can work, but most
likely there will be specific cases that the programmer did not take into account. And then the hacker, having the code,
and sometimes not even having it, can understand what problems there may be in the software and use it for hacking.
Basically, these are problems related to arrays in which data is stored, namely transitions beyond the boundaries of
arrays, which gives the hacker the opportunity to perform operations that were not originally intended.

_- What are the ways to prevent these mistakes?_

There are many source and binary code analysis tools that allow you to find these errors. However, it is impossible to
solve the problem completely: not all available mechanisms can identify certain problems. There are two main approaches:
static analysis, when the tool "looks" at the source/binary code of the program and determines whether there is an error
or not, and dynamic analysis, which runs the program and looks at whether the program behaves correctly or not. Both
static and dynamic analysis tools are being developed in the Center of Advanced Software Technologies of the RAU in the
direction of program analysis.

_- How is your development better than the available alternatives?_

Before starting to develop something, we do a detailed analysis, during which we understand what limitations existing
mechanisms have. And already when developing a specific tool, we try to eliminate the limitations that current tools
have, which gives us a competitive advantage.

If we talk about hacker attacks, then we can distinguish them by categories and the level of training of "specialists /
hackers". So, for the implementation of primitive attacks, it is quite possible to use ready-made tools. Such an arsenal
is used by specialists / hackers of a low level. But there are specialists of the second level: there are few of them,
each of them is worth its weight in gold. These guys know how to find vulnerabilities and exploit them first.

Of course, first of all it is necessary to train qualified specialists who will be able to protect against well-known
vulnerabilities, and then think over a strategy of actions to strengthen the potential of human resources and train
specialists who will be able not only to protect, but also to solve some other tasks.

_- More recently, the Rust programming language has begun to gain popularity. Do you think it will be able to displace
classic C and C++?_

It should be understood that the C language appeared in the early 70s, and the C++ language in the early 80s. And over
these 40-50 years, a lot of codes have been written in these languages. Mobile phone and computer operating systems and
many other applications are written mainly in C and C++. This is many years of work, and no one can just take and
replace billions of lines of source code.

It is noteworthy that Rust has the ability to announce an unsafe code segment. And if you study various projects, you
can see a lot of code fragments that are declared as "unsafe". These are the places where an attack can be carried out.

_- There is a widespread opinion in society that programmers do not need mathematics. Is it so?_

This opinion is incorrect. 600-700 bachelors in the field of IT who studied programming are graduated annually
throughout Armenia, 200 thousand in India, and more than 300 thousand in China. And if you don't study mathematics, then
it will be difficult to compete with them, to put it mildly. This is taking into account the fact that salaries there
are on average 3-4 times less than in Armenia.

If you want to be competitive programmers, IT specialists, you need to study mathematics. You can't make quality
products without mathematics. Tasks for which mathematics is not needed are most likely related to web programming, some
aspects of mobile programming. I think that in the coming years, artificial intelligence-based tools will appear in this
segment, which will easily solve the tasks set. And then the guys who did not study mathematics or thought that
mathematics was not very important will be the first to "exit" the game (they will be replaced by AI). Therefore, all
students who study today should understand that mathematics is mandatory.

_- Recently, we have witnessed a large influx of IT specialists from Russia. How has this affected the Armenian economy
and the market as a whole?_

Each change has positive and negative sides. If you look from the point of view of the IT industry and the economy, then
this is most likely a plus. Visitors settled here, pay taxes, spend money, go to cafes and restaurants, etc.
International organizations predicted 3-4% growth in the economy, and in the end we recorded more than 14%. But there
are also negative sides. So, the rent for living space has increased significantly.

_- Recently, code completion tools with the use of artificial intelligence have begun to gain popularity. Is it possible
in the future to completely or partially replace human AI?_

Partial replacement of human resources by artificial intelligence mechanisms is already happening today. It won't be
possible to completely replace it in the near future, but quite a few aspects of programming will be replaced. The main
message is to study mathematics and deal with complex problems, which artificial intelligence, I think, will not be able
to solve in the coming decades.

_- How are IT technologies used in education?_

IT technologies are widely used in education, ranging from systems and platforms that allow online lessons, video
lectures, etc. Popular technologies that allow you to "unload" the teacher, for example, to carry out automatic
verification of certain tasks, tests. Moodle systems and other online learning platforms allow you to create content and
train hundreds of people at once, with limited resources.

{{< rawhtml >}}
<img src="/images/sevak-sargsyan-interview/img.webp"/>
{{</ rawhtml >}}

_- What is the most popular field in IT right now, is there any interest in system programming?_

Web programming and mobile programming are very popular in Armenia. To solve serious problems , many companies use .NET
Framework, JavaScript and technologies related to it.

Unfortunately, I should note that interest in system programming is quite low. In principle, this is logical: Armenia is
a small country, the market here is also small. Therefore, many of our specialists work for foreign companies.