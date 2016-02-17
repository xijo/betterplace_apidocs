
# Fundraising Event List ⇄ [Details](fundraising_event_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/fundraising_events.json?facets=tax_deductible%3Atrue&order=rank%3ADESC&q=Die+Eckerts&scope=location
```

A list of betterplace.org fundraising events (donate money).
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**
Use this resource like `/clients/PERMALINK/fundraising-events.json`


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">scope</th>
    <td><code>location</code></td>
    <td>no</td>
    <td>Use the scope to specify how the search-query <code>q</code> should behave:
<ul>
<li>"no scope" (default) performs a full text search
<li><code>human_name</code> searches only on the manager-fullname and carrier-fullname.
  Use this to get all entities by "Unicef" or by "Till Behnke".
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Die Eckerts</code></td>
    <td>no</td>
    <td>Search query. The searches behaviour is based on the scope.</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>tax_deductible:true</code></td>
    <td>no</td>
    <td>Filter the result set.
Documented and supported filters are:
<ul>
<li><code>tax_deductible:true/false</code>
<li><code>prohibit_donations:true/false</code>
</ul>
It is possible to set multiple facet filters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>rank:DESC</code></td>
    <td>no</td>
    <td>Order the results by <code>score</code> (only when a query (q) is given),
<code>rank</code>, <code>id</code>, <code>progress_percentage</code>,
<code>tax_deductible</code>, <code>created_at</code>, <code>updated_at</code>,
<code>last_donation_at</code>, <code>completed</code>.
Use the optional <code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
<br>
The default order is the same as for the
<a href="https://www.betterplace.org/en/projects/list?search_form%5Bfilters%5D%5Btype%5D=Group">betterplace.org fundraising events list</a>:
<code>completed:asc| score:desc | rank:desc| last_donation_at:desc</code>
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
      <td>number</td>
      <td>1</td>
      <td>An integer number ≥ 1</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td>string</td>
      <td>Gemeinsam gegen Ebola: Deine Spende für Westafrika</td>
      <td>Max 50 character</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td>Lorem ipsum</td>
      <td>Max 25.000 character</td>
    </tr>
    <tr>
      <th align="left">tax_deductible</th>
      <td>boolean</td>
      <td>true</td>
      <td>True if the fundraising event is marked as tax deductible and
can only support tax deductible projects.
If so, users can request a tax-receipt for their donation
that can be used with the german tax authorities.
</td>
    </tr>
    <tr>
      <th align="left">donations_prohibited</th>
      <td>boolean</td>
      <td>false</td>
      <td>True if the fundraising event must not and cannot receive donations.
This might happen if the event was closed by the manager
or blocked by a platform administrator.

Please check this flag whenever you display a donation button.
Should you show a button for an event that cannot receive donations
the user will open the donation form and see an error message on
betterplace.org instead!
</td>
    </tr>
    <tr>
      <th align="left">closed_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the fundraising event was closed
by the manager.
</td>
    </tr>
    <tr>
      <th align="left">donor_count</th>
      <td>number</td>
      <td>46</td>
      <td>Number of unique donors, based on the payment-email-address</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>232323</td>
      <td>How many cents were already raised with the fundraising event</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td>number</td>
      <td>12382</td>
      <td>How many cents were requested to be raised with the fundraising event.
This value is optional! The manager decides if his event has a goal or not.
</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td>number</td>
      <td>5</td>
      <td>% financed. This value is only present in case the manager
decided to add a <code>requested_amount_in_cents</code>.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>The public face of the fundraising event / fundraising event manager</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td>null &#124; object</td>
      <td>//asset1.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</td>
      <td>TODO</td>
    </tr>
  </table>
### <a id="contact" href="#contact-ref">↑Nested Attributes: contact</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.name</th>
      <td>null &#124; string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke".

In the case of donation-opinions the name might also be
empty/null for anonymous donations for anonymous donations.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact.picture-ref" href="#contact.picture">
            ↓contact.picture
          </a>
        </th>
      <td>string</td>
      <td>//asset1.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</td>
      <td>User profile picture or a fallback image</td>
    </tr>
  </table>
### <a id="contact.picture" href="#contact.picture-ref">↑Nested Attributes: contact.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.picture.fallback</th>
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
    </tr>
  </table>
### <a id="profile_picture" href="#profile_picture-ref">↑Nested Attributes: profile_picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">profile_picture.fallback</th>
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
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
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="fundraising_event_details.md">fundraising event details</a>)
</td>
    </tr>
    <tr>
      <th align="left">featured_projects</th>
      <td>A list of <a href="projects_list.md">projects</a> are currently supported by the fundraising event.

Please note, that this project list has no fixed relation to the list of projects that received money by this fundraising event (see <a href="fundraising_events_featured_projects_list.md">Featured Projects List</a>).
A Fundraising event manager can change the list of supported projects at any time; regardless if they received money before.
</td>
    </tr>
    <tr>
      <th align="left">forwardings</th>
      <td>Provides a list of forwarded amounts and their receiving projects.

Each fundraising event can have multiple projects that it supports. The fundraising event manager specifies the amount that is forwarded from the fundraising event to the project.
Please note, that this list of forwarded donations and their corresponding receiving projects is not required to be in sync with the <a href="fundraising_events_featured_projects_list.md">Featured Project List endpoint</a>.
To find out, if all donations of the fundraising event have been forwarded, please sum the amounts provided by this api endpoint and compare it to the donated amount attribute of the fundraising event api endpoint.
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">new_client_donation</th>
      <td>Link to the donation form. Templated, needs insertion of the client_id.
</td>
    </tr>
    <tr>
      <th align="left">new_donation</th>
      <td>Link to the regular donation form.
</td>
    </tr>
    <tr>
      <th align="left">contact.platform</th>
      <td>The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.
</td>
    </tr>
    <tr>
      <th align="left">contact.contact_data</th>
      <td>The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.
</td>
    </tr>
    <tr>
      <th align="left">contact.picture.fill_100x100</th>
      <td>100×100 Pixel</td>
    </tr>
    <tr>
      <th align="left">contact.picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_960x500</th>
      <td>950×500 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_730x380</th>
      <td>730×380 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_618x322</th>
      <td>618×322 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_410x214</th>
      <td>410×214 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_270x141</th>
      <td>270×141 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">profile_picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 4638,
  "offset": 0,
  "total_pages": 1546,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 3457,
      "created_at": "2010-04-28T17:20:10+02:00",
      "updated_at": "2016-02-08T14:56:39+01:00",
      "title": "\"Mail raus&Attachment vergessen? 1Euro!\"",
      "description": "Wir alle machen mal Fehler. Sie zu vermeiden lernt man am besten durch eine kleine Strafe - in diesem Fall einer Spende von einem Euro. Also: Alle die Euch eine Mail schicken, in der das Attachment vergessen wurde, müssen von Euch den Link zu diesem Fundraising-Team gemailt kriegen - und dann einen Euro spenden. Damit schön viel Geld für einen guten Zweck zusammen kommt und von betterplace.org zu 100 Prozent weitergeleitet wird. Und damit alle Attachmentvergesser endlich aus ihren unverzeihlichen Fehlern lernen.",
      "tax_deductible": true,
      "donations_prohibited": false,
      "closed_at": null,
      "donor_count": 113,
      "donated_amount_in_cents": 35100,
      "requested_amount_in_cents": null,
      "progress_percentage": null,
      "contact": {
        "name": "Moritz E.",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/000/006/fill_100x100_original_eckert.png"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/000/006/crop_original_original_eckert.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/moritz_e"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/6/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/003/457/fill_960x500_original_Bildschirmfoto_2010-04-28_um_17.25.56.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/003/457/fill_730x380_original_Bildschirmfoto_2010-04-28_um_17.25.56.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/003/457/fill_618x322_original_Bildschirmfoto_2010-04-28_um_17.25.56.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/003/457/fill_410x214_original_Bildschirmfoto_2010-04-28_um_17.25.56.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/003/457/fill_270x141_original_Bildschirmfoto_2010-04-28_um_17.25.56.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/003/457/crop_original_original_Bildschirmfoto_2010-04-28_um_17.25.56.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/3457.json"
        },
        {
          "rel": "featured_projects",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/3457/featured_projects.json"
        },
        {
          "rel": "forwardings",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/3457/forwardings.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/3457-mail-raus-attachment-vergessen-1euro"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/3457/client_donations/new?client_id=%7Bclient_id%7D",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/3457/donations/new"
        }
      ]
    },
    {
      "id": 4851,
      "created_at": "2010-10-22T11:00:26+02:00",
      "updated_at": "2013-09-23T21:37:50+02:00",
      "title": "SAT.1 Brautkleid-Verlosung aus Anna und die Liebe",
      "description": "Liebe Freunde von Anna und die Liebe!<br><br>Schön, dass Ihr zusammen mit SAT. 1 lernschwächeren Kindern in Berlin wirksam helfen wollt. Spendet jetzt ein paar Euro: <br><br>UNTER ALLEN SPENDERN WIRD MIAS ORGINAL BRAUTKLEID AUS \"Anna und die Liebe\" VERLOST*! <br><br>Die Spenden, die so mit dieser Aktion hier über betterplace.org gesammelt werden, fließen zu 100 Prozent an den gemeinnützigen Berliner Verein \"Hand in Hand Patenschaft e.V.\". Die helfen damit Kindern, die zwar sehr motiviert sind, es trotz großer Anstrengungen aber nicht schaffen in der Schule mitzuhalten.<br><br>Vielen Dank für Eure Spenden - auch im Namen der Kinder in Berlin.<br><br>Moritz Eckert,<br>Mitgründer betterplace.org<br><br>* Du willst das orginal Brautkleid aus \"Anna und die Liebe\" gewinnen? So nimmst Du an der Verlosung teil:<br>- Spende auf dieser Seite an die Aktion \"Brautkleid-Verlosung aus Anna und die Liebe\"<br>- ...oder sende eine SMS mit dem Kennwort KLEID an die Nummer 81190 (5 Euro gehen an den Verein \"Hand in Hand Patenschaft e.V.\"). Die Charity-SMS kostet 5,17 € (ggfs. zzgl. der Kosten für eine normale SMS)<br>- ...oder schreibe eine E-Mail an die Adresse \"change@betterplace.org\" mit dem Betreff: \"Hilfe für lernschwache Kinder\".<br>Alle, die bis Freitag, 05.11. 2010, 08:30 Uhr über einen der drei genannten Wege an der Verlosung teilnehmen, haben die Chance das Brautkleid zu gewinnen. Der Rechtsweg ist ausgeschlossen.<br><br>Zu guter Letzt - die Details des Brautkleides:<br>- Das Kleid misst von der Schulter bis zum Boden 155 cm<br>- Die Rocklänge beträgt ab der Taille bis zum Boden 116 cm<br>- Die Corsagenlänge: Seite 25 cm, vorne 34 cm<br>- Die Taille: 78cm (also eine Konfektionsgröße 38/40)<br>- BH Größe 80B<br><br>Mehr Infos gibt es auch noch unter: http://www.sat1.de/annaunddieliebe/",
      "tax_deductible": true,
      "donations_prohibited": false,
      "closed_at": null,
      "donor_count": 120,
      "donated_amount_in_cents": 931200,
      "requested_amount_in_cents": null,
      "progress_percentage": null,
      "contact": {
        "name": "Moritz E.",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/000/006/fill_100x100_original_eckert.png"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/000/006/crop_original_original_eckert.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/moritz_e"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/6/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/004/851/fill_960x500_original_brautkleid.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/004/851/fill_730x380_original_brautkleid.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/004/851/fill_618x322_original_brautkleid.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/004/851/fill_410x214_original_brautkleid.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/004/851/fill_270x141_original_brautkleid.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/004/851/crop_original_original_brautkleid.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/4851.json"
        },
        {
          "rel": "featured_projects",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/4851/featured_projects.json"
        },
        {
          "rel": "forwardings",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/4851/forwardings.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/4851-sat-1-brautkleid-verlosung-aus-anna-und-die-liebe"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/4851/client_donations/new?client_id=%7Bclient_id%7D",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/4851/donations/new"
        }
      ]
    },
    {
      "id": 26452,
      "created_at": "2016-01-07T21:47:49+01:00",
      "updated_at": "2016-02-15T16:51:17+01:00",
      "title": "Warme Füße für alle!",
      "description": "Wir sammeln Geld für die Obdachlosenhilfe in Berlin und freuen uns über eure Unterstützung!<br><br>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++<br><br>Frohes Neues nachträglich! Falls ihr in den letzten Tagen eure beheizten Gemächer verlassen haben solltet, könnte euch folgender Fakt um die Ohren geweht sein: Es ist verdammt kalt! Keine besonders schöne Vorstellung, bei diesem arktischen Klima im Freien übernachten zu müssen. Doch leider ist genau das für einige Menschen bittere Realität. Das Thema Obdachlosigkeit fristet leider immer noch ein viel zu wenig beachtetes Schattendasein am äußersten Rande unserer Gesellschaft. Das möchten wir gerne im Rahmen unserer bescheidenen Mittel ändern.<br><br>Warum leben in einem Staat mit Sozialsystem überhaupt Menschen auf der Straße? Die Gründe dafür sind so unterschiedlich wie die Menschen selbst: Drogenmissbrauch, Verschuldung, abgewiesene Asylanträge, Depressionen oder andere psychische Erkrankungen ... Gerade in Berlin ist der Wohnungsmarkt durch die stetige Gentrifizierung sehr angespannt, so dass auch immer wieder Menschen wohnungslos werden, obwohl sie in einer festen Arbeit oder Ausbildung sind. Fakt ist - wenn man einmal auf der Straße gelandet ist, ist es verdammt schwer wieder in die Gesellschaft zurück zu finden. Ein Leben ohne Dach über dem Kopf ist menschenunwürdig.<br><br>Darum haben wir zusammen mit unseren Freunden vom „mob e.V.“ und „Strassenfeger\" die Aktion „Warme Füße für alle!“ ins Leben gerufen. Unser Ziel ist es, ein paar überschüssige Euros in konkrete Projekte zu bringen, die die Lebenssituation von Menschen ohne Obdach über die kalte Jahreszeit ein wenig besser machen können. Der „Strassenfeger\" dürfte einigen von euch schon aus U-Bahnen und Restaurants bekannt sein. Obdachlose verkaufen die Zeitung, um mit ihrem Teil der Einnahmen ihr Leben zu finanzieren. Aber die Organisatoren unter dem Dach des „mob e.V.“ betreiben noch viele weitere Institutionen, die Hilfeleistungen für Wohnungslose anbieten. Darunter fallen eine Notunterkunft mit Dusch- und Schlafmöglichkeiten, ein Café mit preisgünstigem Speiseangebot und beheiztem Aufenthaltsbereich, ein Sozialwarenkaufhaus, in dem Bedürftige und sozialschwache Menschen günstig Möbel etc. erwerben können, sowie kostenlose Sozialberatung und Rechtsbeistand für alle Fälle. Der Grundgedanke des Vereins ist Hilfe zur Selbsthilfe: Obdachlosen wieder auf die Beine helfen und ihren harten Weg zu einem Leben mit Wohnung und Job begleiten. Auch immer mehr Rentner, Hartz IV-Empfänger, Sozialhilfeempfänger u.a. wenden sich aufgrund ihrer schlechten Situation an den mob e.V.<br><br>Das ist viel Arbeit und ein immenser logistischer Aufwand. Man kann nicht müde werden zu betonen, dass das fast alles ehrenamtlich geschieht. Die Mädels und Jungs vor Ort sind dementsprechend auf jeden Euro angewiesen. Und da kommt ihr ins Spiel! Seid doch so nett und lasst hier ein bisschen von eurem Weihnachtsgeld liegen, damit auch die Menschen außerhalb der Komfortzone mit unserer gemeinsamen Hilfe einen menschenwürdigen Winter verbringen können. Es wäre uns eine wahnsinnige Freude, wenn ihr euch beteiligt!<br><br>WARME FÜSSE FÜR ALLE!<br><br>Eure Rostocks",
      "tax_deductible": true,
      "donations_prohibited": false,
      "closed_at": null,
      "donor_count": 238,
      "donated_amount_in_cents": 711464,
      "requested_amount_in_cents": 1000000,
      "progress_percentage": 71,
      "contact": {
        "name": "Jennifer Rostock ..",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/475/586/fill_100x100_11261712_10153030549016010_9015987122739319188_n.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/475/586/crop_original_11261712_10153030549016010_9015987122739319188_n.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/johannes_w36"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/475586/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/026/452/fill_960x500_Warme_F__e_betterplace_2.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/026/452/fill_730x380_Warme_F__e_betterplace_2.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/026/452/fill_618x322_Warme_F__e_betterplace_2.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/026/452/fill_410x214_Warme_F__e_betterplace_2.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/026/452/fill_270x141_Warme_F__e_betterplace_2.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/026/452/crop_original_Warme_F__e_betterplace_2.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/26452.json"
        },
        {
          "rel": "featured_projects",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/26452/featured_projects.json"
        },
        {
          "rel": "forwardings",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/26452/forwardings.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/26452-warme-fusse-fur-alle"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/26452/client_donations/new?client_id=%7Bclient_id%7D",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/26452/donations/new"
        }
      ]
    }
  ]
}
```

