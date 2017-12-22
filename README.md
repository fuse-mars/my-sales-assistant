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

**NOTE** that this is just a way of designing a bot, so I am sure it can be used to create bots in other frameworks! 
 
* Intents

As described above, the bot can with intention of *Finding a restaurant*

So we have one intent, which is basically the **Task** that our bot can permorm.

We call it **findRestaurants** Intent

* Entities

In order to find restaurants, the bot will need to get some information from the user (as our function above requires)

These pieces of information are extracted from the user's message and stored as **Entities**

Example would be something like below, if user says `find me a vegetarian restaurant in Manhattan`

```typescript
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

* Utterances

find me vegetarian restaurants in Manhattan


## Implementation
