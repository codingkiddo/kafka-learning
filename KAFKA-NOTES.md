


Hi, this is Vinod Kumar from CodingKiddo, and welcome to this course in the Apache Kafka Series, Kafka for Beginners.

And this is the third edition of this course, so by this time, this course should be really good for you.

So here's a course introduction. Please don't skip it.

I'm gonna go over some important information.

So, first of all, welcome to the course.

I'm really excited to have you here.

And by now, over 130,000 students have done this course.

I've received more than 30,000 reviews,

and I've iterated upon these reviews

to really, over time, keep on improving this course.

And this is a all new, fresh recording.

So after all the feedback I received,

I wanted to reorganize some lectures.

I'm going to give you more real life exercises.

So you have some really cool examples

in this course, added some sections, some lectures

and I've updated two version three plus of Apache Kafka

which I think should be compatible even

with version four of Apache Kafka,

but let's see when it comes out.

So happy learning. I hope you're excited.

Now just two intros, please stay here.

So just about me, so you know who I am.

So I am Stephane Maarek,

and I will be your teacher for this course.

I am the co-founder of a company called Conduktor

that I will tell you about on the next slide.

I'm an online instructor on Apache Kafka and AWS.

I used to be on the program committee

of the Kafka Summit in 2019 and 2020

which is the big Kafka conference across the world.

I've made a lot of courses on Apache Kafka,

and I call them via Apache Kafka series.

I wrote blog for Confluent, for Medium, and so on.

You can find me on various channels

GitHub, LinkedIn, Medium, Twitter, and Instagram,

if you wanna follow me based on where you like.

So what is Conduktor?

Conduktor is a company I co-founded

to make Apache Kafka accessible to everyone

because I after teaching Kafka

I was realizing that people still needed help

and needed a desktop graphical UI for Apache Kafka

to use it.

So to see what it looks like,

and from it you can manage Apache Kafka.

You can start Kafka directly as well

from Conduktor in one click.

I will show you how that works in due course.

There's a dark mode for Conduktor.

You can perform all your Kafka development

and operations you'll ever need from this one tool.

It supports every Kafka cluster out there

and all security mechanism, and it supports even

community projects, such as Confluent, Schema Registry

Streams, Connect, ksqlDB, and so on.

So that's it for the intros, I hope you liked it,

and I'm super excited to teach this course to you.

I will see you in the next lecture.



Every enterprise application creates data, whether it consists
of log messages, metrics, user activity, or outgoing messages.
Moving all this data is just as important as the data itself. With
this updated edition, application architects, developers, and
production engineers new to the Kafka streaming platform
will learn how to handle data in motion. Additional chapters
cover Kafka’s AdminClient API, transactions, new security
features, and tooling changes


The first edition of Kafka: The Definitive Guide was published five years ago. At the
time, we estimated that Apache Kafka was used in 30% of Fortune 500 companies.
Today, over 70% of Fortune 500 companies are using Apache Kafka. It is still one of
the most popular open source projects in the world and is at the center of a huge
ecosystem.




# What is event streaming?

Event streaming is the digital equivalent of the human body's central nervous system. It is the technological foundation for the 'always-on' world where businesses are increasingly software-defined and automated, and where the user of software is more software.

Technically speaking, event streaming is the practice of capturing data in real-time from event sources like databases, sensors, mobile devices, cloud services, and software applications in the form of streams of events; storing these event streams durably for later retrieval; manipulating, processing, and reacting to the event streams in real-time as well as retrospectively; and routing the event streams to different destination technologies as needed. Event streaming thus ensures a continuous flow and interpretation of data so that the right information is at the right place, at the right time.


