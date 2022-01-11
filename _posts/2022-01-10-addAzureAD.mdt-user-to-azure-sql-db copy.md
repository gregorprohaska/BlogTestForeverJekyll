---
layout: post
title: new Adding an Azure AD (Guest) user to your Azure SQL DB
categories: [Azure, SQL]
---

Hello and welcome. The only purpose of this post is to greet you when your site comes alive for the first time.  
This post will demonstrate some of the more common content & elements found in posts.  
Feel free to delete this post when you are ready to publish your first post.  

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit.

In one of my last projects we had to add Azure AD Guest Users to an Azure SQL DB which was hosted in our tenant. Luckily creation of guest users within our tenant was already enabled, Azure Subscription was associated to an Azure Active Directory and therefore we could concentrate on adding such users to our Azure SQL DB (as will this post).

## Enabling Azure AD authentication
Before you can add an Azure AD user Azure AD authentication has to be enabled on this instance\server of Azure SQL DB. 


Check "Support only Azure Active Directory authentication for this server" if you would like to restrict access to AAD-Users only(similar to "Windows Authentication mode" in an on-prem setup).

## Adding Azure AD (guest) user
To be honest: it really doesn't matter if you would like to add a guest user or an user of your tenant.

Just connect to your Azure SQL DB with your Azure AD admin and create the user via t-sql.
"FROM EXTERNAL PROVIDER" indicates that this is an Azure AD user.
As soon as this is done the user should be able to connect to the database. **BUT** this user does not have any access rights to this database. You could add this user to a role (e.g. db_datareader, db_owner,...) or explicitly grant access to specific objects.
