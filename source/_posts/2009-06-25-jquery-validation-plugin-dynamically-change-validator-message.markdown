---
comments: true
date: 2009-06-25 21:43:12
layout: post
slug: jquery-validation-plugin-dynamically-change-validator-message
title: jQuery Validation Plugin – Dynamically change validator message
wordpress_id: 209
categories:
- jQuery
tags:
- jQuery Validation Plugin
---

#### **       
UPDATE:** Please read [Guu](http://gusgus.wordpress.com/)’s comment below for a far better solution to this problem!

 

I’ve been using the [jQuery Validation Plugin](http://docs.jquery.com/Plugins/Validation) and needed to change a validation message dynamically based on the user input. I had a quick search but couldn’t find an easy solution. Unfortunately the messages are not changeable after the initial construction of the validator object. I managed to get around the problem by removing the validator an then re-adding with a new message:

 

## Create validator

 

$("#Enquiry").validate({     
rules: {      
EnquiryText: { required: true }      
},      
messages: {      
EnquiryText: "Enquiry must contain an entry."      
}      
});

 

## Dynamically change message

 

function setEnquiryValidationTo(message) {     
$("#EnquiryText").rules("remove");      
$("#EnquiryText").rules("add", {      
required: true,      
messages: {      
required: message      
}      
});      
} 

 

There may be a better/easier way to do this but I couldn’t find one via Google.
