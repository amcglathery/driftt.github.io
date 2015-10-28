---
layout: page
title: HTTP-API
permalink: /http-api/
show_in_nav: true
links:
    - title: What is Driftt
      url: "#whats-driftt"
    - title: Installing
      url: "#installing"
    - title: What it looks like in action
      url: "#in-action"
    - title: Methods
      url: "#methods"
      links:
          - title: identify
            url: "#identify"
          - title: track
            url: "#track"
---

# Driftt HTTP API
The Driftt API makes it dead simple to track events and customer information. Send your customer data through this API and Driftt can become intelligent. We’ll identify what makes a healthy user and empower you to become context-driven when communicating with customers.

<div id="whats-driftt"></div>
## What is Driftt?
Driftt is a customer communication platform that makes it much easier for you and your team to understand, support, and engage with your customers.

<div id="in-action"></div>
## What it looks like in action

You may be a pro at this API stuff, so here’s a short example of how you might use our identify and track calls (both explained below in more detail) in case this is all you need to know and can take it from here.

<div id="methods"></div>
### Methods

<div id="identify"></div>
#### POST `https://event.api.driftt.com/identify`
This method is used to identify users based on their unique user id in your company's user table.

##### Body
```json
{
  "orgId": 1,
  "userId": "019mr8mf4r",
  "attributes": {
    "name": "John Doe",
    "email": "john.doe@gmail.com"
  },
  "createdAt": "1441981033123"
}
```

<table>
  <tbody>
    <tr>
      <td>
        <code>orgId</code>
        <br>
        <em>number</em>
      </td>
      <td>
        The id of your organization in Driftt
      </td>
    </tr>
    <tr>
      <td>
        <code>userId</code>
        <br>
        <em>string, number</em>
      </td>
      <td>
        The unique user ID in your company's user table for the user.
      </td>
    </tr>
    <tr>
      <td>
        <code>attributes</code>
        <br>
        <em>Object, optional</em>
      </td>
      <td>
        A dictionary of attributes you know about this user, such as their <strong>email</strong>, <strong>name</strong>, <strong>company</strong>. We strongly suggest that you pass the <strong>email</strong> attribute.
        <br>
        <strong>Note:</strong> the <code>attributes</code> object <strong>must be</strong> a flat object. Nested objects or arrays will not work
      </td>
    </tr>
    <tr>
      <td>
        <code>createdAt</code>
        <br>
        <em>number, optional</em>
      </td>
      <td>
        the unix timestamp in milliseconds that the event was created at. We will fill it in with the time we recieve the event if you do not pass it.
      </td>
    </tr>
  </tbody>
</table>

<div id="track"></div>
#### POST `https://event.api.driftt.com/track`
This method is what you call to send an event to Driftt. It takes an event name and a list of attributes.

##### Body

```javascript
{
  "orgId": 1,
  "userId": "019mr8mf4r",
  "event": "Link Clicked",
  "attributes": {
    "linkUrl": "http://www.example.com"
  },
  "createdAt": "1441981033123"
}
```
<table>
  <tbody>
    <tr>
      <td>
        <code>orgId</code>
        <br>
        <em>number</em>
      </td>
      <td>
        The id of your organization in Driftt
      </td>
    </tr>
    <tr>
      <td>
        <code>userId</code>
        <br>
        <em>string, number</em>
      </td>
      <td>
        The unique user ID in your company's user table for the user.
      </td>
    </tr>
    <tr>
      <td>
        <code>event</code>
        <br>
        <em>string</em>
      </td>
      <td>
        This is the name of this type of event. You should try to reuse the same events with different properties to describe similar actions such as <strong>Share</strong> or <strong>Link Clicked</strong>
      </td>
    </tr>
    <tr>
      <td>
        <code>attributes</code>
        <br>
        <em>Object, optional</em>
      </td>
      <td>
        A dictionary of attributes about this type of event, such as <strong>shareType</strong> or <strong>linkUrl</strong>.
        <br>
        <strong>Note:</strong> the <code>attributes</code> object <strong>must be</strong> a flat object. Nested objects or arrays will not work
      </td>
    </tr>
    <tr>
      <td>
        <code>createdAt</code>
        <br>
        <em>number, optional</em>
      </td>
      <td>
        the unix timestamp in milliseconds that the event was created at. We will fill it in with the time we recieve the event if you do not pass it.
      </td>
    </tr>
  </tbody>
</table>