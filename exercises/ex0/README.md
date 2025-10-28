# Getting Started

Before diving into the practical tasks, it’s important to create a clear plan. This involves identifying the steps needed to answer the question at hand. While there are technical tasks to complete, conceptual understanding is equally critical. Below is a breakdown of the process:

## Technical Setup

From a technical perspective a few things are important:
- Identify the correct communication scenario
- Establish a connection between SAP S/4HANA Cloud Public Edition and SAP Analytics Cloud (SAC)
- Visualize our data

## Conceptual Considerations

More important than setting up the connection and visualizing the data is asking yourself first, what data I actually need to solve my problem. The communication scenario we are using is a good exmaple for this. When looking at the fields, there is no field which would give a direct answer – for example, something like "when was the connection used last."

To do this, the first thing you want to do is look at the API and the information it returns. The easiest way is to view the **Schema** of the API here: https://api.sap.com/api/CE_COMMUNICATIONUSER_0001/schema

You will notice that the best field to use is based on the user: there is a field called **LastLogonDateTime** - if this is not populated, the user has never logged on, and hence the communication arrangement most likely has never been used. 

>**Note**: Of course, someone could have used the connection and changed the user afterwards, which is why you would want to integrate other fields, such as when was the connection last changed, in order to get the real picture, but for the sake of simplicity we will stick to this one field for this exercise. 

To visualize the unused connections, there are different options as well. For this exercise, we will use a fairly simple visualization: comparing the number of users who have logged on with the number of users who have not logged on yet. 

## The Plan

After this preparation, the steps we need to take are clear: 
- Set up a connection to send the communication arrangements from SAP S/4HANA to SAC
- visualize the number of users who have never logged on and compare them with the number of users who have logged on

This is what we will do in the next couple of hours during this workshop. Let's get started!

## Accessing SAP S/4HANA Cloud Public Edition and SAC

Now that we understand what the scope of this hands-on session is, let's check the system access.

1. Search for the internet browser on your computer and navigate to the SAP S/4HANA Cloud Public Edition instance: https://my426786.s4hana.cloud.sap
2. Afterwards, also sign in to the SAC instance in a second tab: https://sacteched25.eu10.hcs.cloud.sap