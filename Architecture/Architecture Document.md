# Architecture Document

## 1. Contents
- [1. Contents](#1-contents)
- [2. Document History](#2-document-history)
- [3. Document Purpose](#3-document-purpose)
- [4. System Architecture](#4-system-architecture)
- [5. Main API Class Diagram](#5-main-api-class-diagram)

## 2. Document History
| Version | Changes | Author | Date |
|---------|---------|--------|------|
| 0.1 | Initial Setup | Ruben Leerentveld | 14-03-2022 | 
| 0.2 | Migration to github | Ruben Leerentveld | 04-04-2022|

## 3. Document Purpose
This document will cover the architecture of the platform. In here you will find a big picture architecture diagram, an architecture diagram of the main api, technology descisions and technology alternatives.

## 4. System Architecture
In this section you can inspect the architecture diagram of the complete platform with a small explaination

![](https://www.plantuml.com/plantuml/png/ROtDQeDG44RtynHVirVeLa98Gw0LAWXr5roCPhJY_P5xnz2-VI-KR1ANt-7CcMDK3hfQGo_wBLPmcxh0JYdEariui4NlxUATEFtINoD8xYlHv5J2mBrWLtsUy5QNEt14LH9LPOPBRLW77op4NHUVx9Os6FByW8-cgGkiKJQDrAeaHXu5NV2pX9OUm7-b4IDZuA70ugFIVIBB3hYKRZ3hp_cKRjyJPCSjzZdkkC0e-fnDhvkfdqKH9TmIeOUDVPQSCojt7AMbexZhQiqV)

- [Platform endpoint] This is the main api, which the frontend communicates with (via HTTP)
- [MLB API]           This is the open source MLB endpoint for getting data
- [Message Broker]    If a order is initiated, the request will be sent to the message broker
- [Telegraf]          Telegraf will send metrics from the Message broker server to InfluxDB
- [Grafana]           Grafana gets data from InfluxDB and visualizes it
- [Ticket Server]     The ticket server handles the order requests
- [Adyen]             Payment is handled via Adyen
- [Database]          This database saves orders and available seats

## 5. Main API Class Diagram

![](https://www.plantuml.com/plantuml/png/pPJRRi8m38Rl-nIvBD9uXGcsIMZQqD0A3v2bfekMGvSOJQZYtPU6GeA5kDnwWspN_lyl1pBpo1tkj2gAOYw4tHbyj0QTLGeScqxlsL1zjOqKHPxaNwll850XH-bH2ayaqeUZIigJq59zp5jP56-k1aVcO-qu6iCqjPRY2p0E2iMzPtGDhYiOwxOIL7rW5_GyI_eU3VXfGzCxD84DtCQ3ApqwQHe6cajrnuQi3KO_rjNdWh1cAvrU3VL9BjVhcvjQmymXBI614VfXgna_XsCa3rWvTx8o851QKyN2ACW7S7fpwSMX5zPVvhdt0d0DN5V0lJNzd2-bGUPZFY6TAyNtu9u00vulJtYn-5nVR_OF-rx_r8mX9kj8N5TEWRVo1VOZ00uUuBPSmF3FxqQpYUG5oZSnUttiEIGEcrPOhOFiWclm9GMeW6Emxp-Ux9iG4zA0AI2wbV5tQMjGHqy2UlkW_vuj7MnwdBj_m9Y1gNTQ_G80)

In the diagram above you can see the structure of the main api (platform endpoint).
The controllers are the endpoints of the api, they each have their own logic. The MlbApi interface is the third party provider that provides statistics. The ticketing api interface connects to the ticket api that I will build myself.
