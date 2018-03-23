
# Project Needs List ⇄ [Details](need_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/projects/1114/needs.json?facets=completed%3Afalse&order=position%3AASC
```

A list of betterplace.org projects needs (donate money).
Results are contained in a *data* attribute.
The details and list view show the same data per project need.

**For [betterplace.org clients](../README.md#client-api):**
There is no client-scoped URL.
Please use the API calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>1114</code></td>
    <td>yes</td>
<td>

Project id as an integer number ≥ 14.

</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>completed:false</code></td>
    <td>no</td>
<td>

Filter the result set.
Documented and supported filters are:
<ul>
  <li><code>completed:true/false</code> – is this need fully funded?
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>position:ASC</code></td>
    <td>no</td>
<td>

Order the result set. Documented and supported orders are:
<ul>
  <li><code>created_at:asc/desc</code> – DESC: Latest needs first.
  <li><code>position:asc/desc</code> – Priority of the need defined by the project manager
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


</td>
  </tr>
</table>


## Response Attributes


### Root Attributes

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>

Max 50 character

</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>



</td>
    </tr>
    <tr>
      <th align="left">completed</th>
      <td><code>boolean</code></td>
      <td><code>false</code></td>
<td>

True if the need is 100 % financed

</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td><code>number</code></td>
      <td><code>82</code></td>
<td>

% financed

</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents are donated already.
This includes all donations that can be given to a need
(direct donation, forwarding of project donation,
forwarding of organisation donation,
forwarding of fundraising event donations,
offline donations and also(!) external donations)


</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents are still needed to complete the need

</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How much money is needed in total

</td>
    </tr>
  </table>
</table>

## Response Links

<table>
  <tr>
    <th>Linkname</th>
    <th>Description</th>
  </tr>
    <tr>
<th align="left">

self

</th>
<td>

Link to this resource itself
(<a href="need_details.md">need details</a>)


</td>
    </tr>
    <tr>
<th align="left">

project

</th>
<td>

Link to the related <a href="project_details.md">project's details</a>


</td>
    </tr>
    <tr>
<th align="left">

new_client_donation

</th>
<td>

Link to the donation form. Templated, needs insertion of the client_id.


</td>
    </tr>
    <tr>
<th align="left">

new_donation

</th>
<td>

Link to the regular donation form.


</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 97,
  "offset": 0,
  "total_pages": 33,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 76625,
      "created_at": "2014-01-03T11:41:44+01:00",
      "updated_at": "2014-03-21T14:35:08+01:00",
      "title": "Kabul Skatepark Food",
      "description": "Equivalent to providing food for the Kabul skatepark for 1 month including the Back-To-School program which runs 5 days/week. The Back-To-School program aims to give children the support they need to return to public school in Afghanistan.",
      "completed": true,
      "progress_percentage": 100.0,
      "donated_amount_in_cents": 74000,
      "open_amount_in_cents": 0,
      "requested_amount_in_cents": 74000,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/needs/76625.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/projects/1114/client_donations/new?client_id=%7Bclient_id%7D&donation_earmark_id=76625",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/projects/1114/donations/new?donation_earmark_id=76625"
        }
      ]
    },
    {
      "id": 79124,
      "created_at": "2014-02-17T17:01:17+01:00",
      "updated_at": "2015-02-26T14:44:31+01:00",
      "title": "Clean Water for the Skateparks in Kabul and MeS",
      "description": "The equivalent of supplying clean drinking water for all of our staff and students in both the Kabul and Mazar-e-Sharif Skateparks. ",
      "completed": true,
      "progress_percentage": 100.0,
      "donated_amount_in_cents": 179500,
      "open_amount_in_cents": 0,
      "requested_amount_in_cents": 179500,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/needs/79124.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/projects/1114/client_donations/new?client_id=%7Bclient_id%7D&donation_earmark_id=79124",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/projects/1114/donations/new?donation_earmark_id=79124"
        }
      ]
    },
    {
      "id": 143000,
      "created_at": "2016-04-06T10:53:18+02:00",
      "updated_at": "2018-01-16T09:50:22+01:00",
      "title": "deutsche version 42;",
      "description": "deutsche version 42;",
      "completed": true,
      "progress_percentage": 100.0,
      "donated_amount_in_cents": 55000,
      "open_amount_in_cents": 0,
      "requested_amount_in_cents": 55000,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/needs/143000.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/projects/1114/client_donations/new?client_id=%7Bclient_id%7D&donation_earmark_id=143000",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/projects/1114/donations/new?donation_earmark_id=143000"
        }
      ]
    }
  ]
}
```

