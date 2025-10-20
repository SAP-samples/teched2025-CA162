The very first thing we need to do is make a plan. In other words, what are the steps we have to take to find the anwer to our question. There are a few technical steps we have to do, but also some conceptual thoughts. Here's how it could be broken down: 

# Technical Setup:
From a technical pperspective a few things are important
- identifying the correct communication scenario
- establishing a connection between SAP S/4HANA Cloud Public Edition and SAC
- Visualizing our data

# Conceptual Thoughts: 

More important than setting up the connection and vizualising the data is asking yourself first, what data I actually need to solve my problem. The communication scenario we are using is a goood exmaple for this. When looking at the fields, there is no field which would give a direct answer, e.g. something like "when was the connection used last".

To do this, the first thing you want to do is look at the API and the information it returns. For this, the easiest is to take a look at the Schema View of the API here: https://api.sap.com/api/CE_COMMUNICATIONUSER_0001/schema

You will notice that the best field to use is based on the user: there is a field called LastLogonDateTime - if this is not populated, the user has never logged on and hence the communication arrangement most likely has never been used. 

** note: of course, someone could have used the connection and changed the user afterwards, which is why you would want to integrate other fields, such as when was the connection last changed, in order to get the real picture, but for the sake of easiness we will stick to this one field for this exercise. 

To visualize the unused connections, there are different options as well. For this exercise we will use a fairly simple visualization: comparing the number of users who have logged on with the number of users who have not logged on yet. 

# The plan

After this preparation, the steps we need to take are clear: 
- Set up a connection to send the communication arrangements from SAP S/4HANA to SAC
- visualize the number of users who have never logged on and compare them with the number of users who have logged on. 

This is what we will do in the next couple of hours during this workshop. Let's get started.
