---
layout: page
title: SDK
permalink: /sdk/
redirect_from: /
show_in_nav: true
links:
    - title: What is Driftt
      url: "#whats-driftt"
    - title: Installing
      url: "#installing"
    - title: What it looks like in action
      url: "#in-action"
      links:
          - title: HTML Example
            url: "#html-example"
    - title: Methods
      url: "#methods"
      links:
          - title: identify
            url: "#identify"
          - title: track
            url: "#track"
          - title: debug
            url: "#debug"
---

# Driftt JS SDK
The Driftt SDK makes it dead simple to track events and customer information. Send your customer data through this SDK and Driftt can become intelligent. We’ll identify what makes a healthy user and empower you to become context-driven when communicating with customers.

<div id="whats-driftt"></div>
## What is Driftt?
Driftt is a customer communication platform that makes it much easier for you and your team to understand, support, and engage with your customers.

<div id="installing"></div>
## Installing
Log into your Driftt account and head to the [JS SDK integrations page](https://app.stage.driftt.com/integrations/install). Then copy and paste the html snippet inside your webpage's, or web app's, `<head>` block.
To make life easy for you, this JS snippet will never change... after installing this you’ll never have to touch it again no matter how many new features we release.

<div id="in-action"></div>
## What it looks like in action

You may be a pro at this API stuff, so here’s a short example of how you might use our identify and track calls (both explained below in more detail) in case this is all you need to know and can take it from here.

<div id="html-example"></div>
#### HTML Example
```
<!-- html webpage -->
<script>
driftt.identify(userId, { email: 'abcd@email.com' });
</script>
```

```
<div onClick="driftt.track('Clicked Div', { name: 'awesomeDiv' })">
Click
</div>
```
<div id="methods"></div>
### Methods

<div id="identify"></div>
#### identify
This method is used to identify users based on their unique user id in your company's user table.

**Note:** the attributes object **must be** a flat object:

```
driftt.identify('USER_ID_1');
driftt.identify('USER_ID_2', { email: 'example@example.com' });
driftt.identify('USER_ID_2', { email: 'example@example.com', phoneNumber: '5-555-555-5555' });
```

Nested objects or arrays will **not** work, such as the following:

```
driftt.identify('USER_ID_1', { emails: ['example@example.com', 'example@gmail.com'] });
```

You can also use the identify call to update info about the user via the `attributes` parameter.

```
driftt.identify([userId], [attributes]);
```

<table>
  <tbody>
    <tr>
      <td>
        <code>userId</code>
        <br>
        <em>string/number</em>
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
        A dictionary of attributes you know about this user, such as their <strong>email</strong>, <strong>name</strong>, <strong>company</strong>.
        <br>
        <strong>Note:</strong> the <code>attributes</code> object <strong>must be</strong> a flat object. Nested objects or arrays will not work
      </td>
    </tr>
  </tbody>
</table>

<div id="track"></div>
#### track
This method is what you call to send an event to Driftt. It takes an event name and a list of attributes.

**Note:** As explained in the identify call, the `attributes` object must be a flat object; nested objects or arrays won’t work

```
driftt.track('Page Loaded');
driftt.track('Exported', { exportedObject: '2015_users' });
driftt.track('Shared Content', { contentId: 1, contentName: 'Proposal', contentType: 'document', method: 'Email' });
```

```
driftt.track([event], [attributes]);
```

<table>
  <tbody>
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
  </tbody>
</table>

<div id="debug"></div>
#### debug
This method is what you call to enable or disable debug mode for the Driftt sdk. Debug mode means that more logging will be output to console and that all events sent won't contaminate non-debug data. `debug` takes an optional boolean that enables or disables debug mode which if omitted will also enable debug mode.

```
driftt.debug();
driftt.debug(true);
driftt.debug(false);
```

```
driftt.debug([enabled]);
```

<table>
  <tbody>
    <tr>
      <td>
        <code>enabled</code>
        <br>
        <em>boolean, optional</em>
      </td>
      <td>
        An optional boolean that enables or disables debug mode. If omitted then calling this method will enable debug mode.
      </td>
    </tr>
  </tbody>
</table>