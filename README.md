# my-search-assistant

## Design

* **Main Task:** 

Create a bot that helps people find a good restaurant to eat at.

* What users want to do

Below is an example of what the user might type when they want the bot to complete the *Main task*

```sh
Hi bot, find me a vegetarian restaurant in Manhattan
```

* What developers undertand

We developers prefer requirements expressed in terms of *input* and *output* or simply **What is the user going to do and what is my program going to give them back**

Below is our *Main task* expressed in code
```typescript
findRestaurants(
  location: {latitude: number, longitude: number},
  pricaRange: {min: number, max: number},
  acceptCard: boolean,
  serveVegetarian: boolean
 ) => Array<{
    name: string,
    phone: string,
    website: string,
    location: {latitude: number, longitude: number},
    photo: string
 }>
 ```
 
 Below, we are going to see how LUIS and Botframework from Microsoft, helps us go from **What users want to do** to **What developers undertand**

**NOTE** that this is just one way of designing a bot, so it can be used to create bots in other frameworks!

## LUIS

LUIS allows the bot to undertand the user's message. It provides this understanding through a few keys concepts defined below.
 
### Intents

As described at the top, the bot can be used with intention of *Finding a restaurant*

So we have one intent, which is basically the **Task** that our bot can perform.

We call it **findRestaurants** Intent

Example of what the bot will receive, would be something like below, if user says `find me a vegetarian restaurant in Manhattan`

```typescript
{
  query: 'find me a vegetarian restaurant in Manhattan',
  intents: [{
    intent: 'findRestaurants',
    score: 0.99999999
  }]
}
```

### Entities

In order to find restaurants, the bot will need to get some information from the user (as our function above requires)

These pieces of information are extracted from the user's message and stored as a list of **Entities**

Example would be something like below, if user says `find me a vegetarian restaurant in Manhattan`

```typescript
// ... query and intents 
[{
  entity: 'vegetarian',
  type: 'ServiceOptions',
  resolution: {
    serveVegetarian: true
  }
},{
  entity: 'Manhattan',
  type: 'Location',
  resolution: {
    location: { latitude: 40.7273236, longitude: -73.9884075 }
  }
}]
```

### Utterances

Since LUIS is a machine, you have to *teach* it how to *understand* and *exract userful information* from the user message.

You (as a developer) teach this machine by providing different messages that you think the user might send, and specifying which *Intent* these messages are bound to

Examples can be similar to below sentences, if user says `find me a vegetarian restaurant in Manhattan`

* **what is the best place to eat vegetarian food**, *Intent is findRestaurants*
* **restaurants with vegetarian menu** => *Intent is findRestaurants*
* **vegetarian restaurants** => *Intent is findRestaurants*
* **Top rated restaurants in Manhattan** => *Intent is findRestaurants*


Some technical terms
* teach = **Train**
* understand = **Intent Recognition**
* exract userful information = **Entity Extraction**

At this point, the bot has partial information that allows it to map **What users want to do** to **What developers undertand**

## Botframework

### 


## Implementation
