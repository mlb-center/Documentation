# Analysis Document

## 1. Contents
- [1. Contents](#1-contents)
- [2. Document History](#2-document-history)
- [3. Document Purpose](#3-document-purpose)
- [4. Product Description](#4-product-description)
- [5. Functional Requirements](#5-functional-requirements)
- [6. Non Functional Requirements](#6-non-functional-requirements)
- [7. Event Storming](#7-event-storming)

## 2. Document History
| Version | Changes | Author | Date |
|---------|---------|--------|------|
| 0.1 | Initial Setup | Ruben Leerentveld | 08-03-2022 | 
| 0.2 | Added Event Storming | Ruben Leerentveld | 12-03-2022 |
| 0.3 | Migration to github | Ruben Leerentveld | 04-04-2022|

## 3. Document Purpose
This document will contain the initial analysis of the MLB Center project. In here you will find the functional and non-functional requirements, corresponding use cases and event storming

## 4. Product Description
I have always been a fan of playing and watching baseball. 
Baseball is the biggest sport in the US. MLB (Major League Baseball) is the professional competition in the US.

The MLB supplies an API where you can retrieve all the data from past games, upcomming games, the leaderboard and player details. I will implement this api in my project.

The idea is to build an web application where you are able to
- See current standings in the league
- Track past games
- Preview upcomming games
- Buy tickets for upcomming games

The ticketing system is where the project gets interesting. I want to use different services to place an ticker order, think of:
- (Self-made) web service for checking available seats
- (Self-made) ticket vending service
- Adyen integration for paying orders
- Mail service to send out bought tickets
- Message queueing to improve performance and scalability
- Telegraf, InfluxDB and Grafana to monitor message queueing

## 5. Functional Requirements
In this chapter the functional requirements are described.
| FR          | Title       | Description |
| ----------- | ----------- | ----------- |
| FR01 | User authentication | Users need to authenticate in order to make use of the platform |
| FR02 | View game results | The platform is able to show game results from the MLB api | 
| FR03 | View upcomming games | The platform is able to show upcomming games from the MLB api | 
| FR04 | Buy tickets | Users are able to buy (fake) tickets for upcomming games |
| FR05 | Third party payment | Payment is done through a third party provider |
| FR06 | Message queueing | Orders are processed through a message broker |
| FR07 | Monitoring | Message queueing will be monitored | 
| FR08 | Monitoring visualization | Data from monitoring will be vizualized |


## 6. Non Functional Requirements
In this chapter the non-functional requirements are described
| NFR   | Title | Description | Tag |
|-------|-------|-------------|-----|
| NFR01 | Account creation | Users need to authenticate to use the platform | Security|
| NFR02 | Password generation | Only Strong passwords are allowed | Security| 
| NFR03 | Navigation | The app needs to be easy to navigate through | Usability |
| NFR04 | Purpose of features | Users can easily determine what a feature is and what it can do | Usability
| NFR05 | Availability group | The platform needs to be deployed on at least 2 availability groups | Availability |
| NFR06 | Code quality | The code needs to be well written to be maintainable | Maintainability |
| NFR07 | Quality check | The code needs to be screened on every push | Maintainability |
| NFR08 | CI/CD | The code needs to be deployed using a CI/CD | Maintainability | 

## 7. Event Storming
To get an idea of what features the platform will need an event storming session is done

[![](https://github.com/mlb-center/Documentation/blob/main/Analysis/img/EventStorm.PNG)
