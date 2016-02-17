
# Volunteering List ⇄ [Details](volunteering_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/volunteering.json?around=10997+Berlin%2C+Germany&nelat=51.123&nelng=12.123&order=created_at%3AASC&q=Homework+help&scope=location&swlat=51.001&swlng=12.001
```

A list of betterplace.org volunteering offers (donate time).
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**
This resource is not avaliable at the moment.


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
<li><code>location</code> does a reverse geocoding lookup.
  This lookup returns a bounding-box. We transform this bounding-box in a
  rectangle that is large enough to encapsulate the whole bounding-box.
  We then return all entities that belong to this rectangle.
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">around</th>
    <td><code>10997 Berlin, Germany</code></td>
    <td>no</td>
    <td>Order the results by the distance to the given location from near to far.
<br>
Location can be provided as …
<br>
<em>… Lat/Lng:</em> <code>52.50,13.45</code>
<br>
<em>… ZIP:</em> <code>10997 Berlin, Germany</code>.
We use the centre of the ZIP code area as center for the search.
Please add enough context information (like the Country name)
so google knows what place you are looking for.
<br>
<em>… any location search:</em> All queries other than a float tuple
are send to the google location service. For the provided response we
take a fitting lat/lng value as center of the search. So in theory,
you can use any search that works for google maps.
<br>
Check the <code>around_location</code> to see what latitude/longitude
values have been used for the query.
</td>
  </tr>
  <tr>
    <th align="left">nelat</th>
    <td><code>51.123</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The northeast corner's latitude.</td>
  </tr>
  <tr>
    <th align="left">nelng</th>
    <td><code>12.123</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The northeast corner's longitude.</td>
  </tr>
  <tr>
    <th align="left">swlat</th>
    <td><code>51.001</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The southwest corner's latitude.</td>
  </tr>
  <tr>
    <th align="left">swlng</th>
    <td><code>12.001</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The southwest corner's longitude.</td>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Homework help</code></td>
    <td>no</td>
    <td>Search query. The searches behaviour is based on the scope.</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>created_at:ASC</code></td>
    <td>no</td>
    <td>Order the result by <code>has_image</code> (default), <code>created_at</code> (second default).
Use the optional <code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
<br>
The default order is the same as for the
<a href="http://www.betterplace.org/en/volunteering/list">betterplace.org volunteering list</a>:
<code>has_image:desc| carrier_has_image:desc| created_at:desc</code>
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
      <th align="left">latitude</th>
      <td>number</td>
      <td>52.499007</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">longitude</th>
      <td>number</td>
      <td>13.44947</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">street</th>
      <td>null &#124; string</td>
      <td>"Schlesische Straße 26"</td>
      <td>Street address</td>
    </tr>
    <tr>
      <th align="left">zip</th>
      <td>null &#124; string</td>
      <td>"10997"</td>
      <td>ZIP code</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td>null &#124; string</td>
      <td>"Berlin"</td>
      <td>Name of the city</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td>null &#124; string</td>
      <td>"Deutschland"</td>
      <td>Name of the country</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td>string</td>
      <td>TODO</td>
      <td>Max 100 character unless the volunteering is imported</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td>TODO</td>
      <td>TODO</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier-ref" href="#carrier">
            ↓carrier
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>An organisation, Users will be added later</td>
    </tr>
    <tr>
      <th align="left">vacancies</th>
      <td>number</td>
      <td>1</td>
      <td>The number of volunteers that are needed, provided by the manager</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="image-ref" href="#image">
            ↓image
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>Each volunteering has one optional image / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>Contact person, contact data and contact address</td>
    </tr>
    <tr>
      <th align="left">topics</th>
      <td>array</td>
      <td>["Development cooperation", "Children & youth"]</td>
      <td>Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "Animal & environment protection", "Culture & sports",
"Children & youth", "Development cooperation ", "DisabledEducation", "Elderly people",
"Human rights", "Refugees & immigrants", "Invalid", "Local help", "Socially deprived"
</td>
    </tr>
    <tr>
      <th align="left">activities</th>
      <td>array &#124; null</td>
      <td>["consulting/coaching", "office work"]</td>
      <td>Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "consulting/coaching", "crafting/gardening", "doing sports",
"doing the chores", "group care", "nursing/parenting", "office work",
"organising/managing", "painting/designing", "tutoring/reading",
"visiting/accompanying", "writing/translating"
</td>
    </tr>
    <tr>
      <th align="left">imported_from</th>
      <td>null &#124; string</td>
      <td>aktion_mensch</td>
      <td>Betterplace imports volunteering offers from Aktions Mensch.</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="import_information-ref" href="#import_information">
            ↓import_information
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>Meta data concerning the import of this volunteering offer, if it
was indeed imported.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td>null &#124; object</td>
      <td></td>
      <td>TODO</td>
    </tr>
  </table>
### <a id="carrier" href="#carrier-ref">↑Nested Attributes: carrier</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.latitude</th>
      <td>number</td>
      <td>52.499007</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">carrier.longitude</th>
      <td>number</td>
      <td>13.44947</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td>string</td>
      <td>"Viva con Agua de Sankt Pauli e.V."</td>
      <td>An organisation name, Users will be added later</td>
    </tr>
    <tr>
      <th align="left">carrier.street</th>
      <td>string</td>
      <td>"Rosenstr. 3"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.city</th>
      <td>string</td>
      <td>"Berlin"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.zip</th>
      <td>string</td>
      <td>"10123"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.country</th>
      <td>string</td>
      <td>"Germany"</td>
      <td>Contact data for the organisation</td>
    </tr>
  </table>
### <a id="image" href="#image-ref">↑Nested Attributes: image</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">image.description</th>
      <td>string</td>
      <td></td>
      <td>Image description</td>
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
      <td>string</td>
      <td>Till Behnke</td>
      <td>Fullname of the contact person.
For imported volunteering offers, this is the
contact-name that is provided on import.
</td>
    </tr>
    <tr>
      <th align="left">contact.phone</th>
      <td>string</td>
      <td>030 - 7676 4488 44</td>
      <td>Phone number for direct contact.
No validations on input apply.
</td>
    </tr>
    <tr>
      <th align="left">contact.email</th>
      <td>string</td>
      <td>support@betterplace.org</td>
      <td>Plain text email-address for direct contact
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact.picture-ref" href="#contact.picture">
            ↓contact.picture
          </a>
        </th>
      <td>string</td>
      <td>//assets.betterplace.org/…</td>
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
### <a id="import_information" href="#import_information-ref">↑Nested Attributes: import_information</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">import_information.created_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the imported record was actually created.
</td>
    </tr>
    <tr>
      <th align="left">import_information.updated_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the imported record was
actually updated last.
</td>
    </tr>
    <tr>
      <th align="left">import_information.import_type</th>
      <td>string</td>
      <td>"Import::ImportFormat"</td>
      <td>Type of import this record originated from.</td>
    </tr>
    <tr>
      <th align="left">import_information.import_id</th>
      <td>string</td>
      <td>"foo:23"</td>
      <td>Unique identifier for this imported record.
</td>
    </tr>
    <tr>
      <th align="left">import_information.imported_at</th>
      <td>string</td>
      <td>"1994-11-15T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the record was imported at
betterplace.
</td>
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
(<a href="volunteering_details.md">volunteering details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">carrier.logo</th>
      <td>The original image version as uploaded by the organisation manager.

Please note: This image might change in the future since this attribute
does not follow the general API pattern for image attributes. You should
subscribe to the change-log newsletter so we can inform you about upcomming changes.
</td>
    </tr>
    <tr>
      <th align="left">image.fill_618x322</th>
      <td>618×322 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.fill_270x141</th>
      <td>270×141 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.original</th>
      <td>Original size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.thumb</th>
      <td>Thumbnail size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.medium</th>
      <td>Medium size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.regular</th>
      <td>Regular size / DEPRECATED, will be removed after 5/2015</td>
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
  "total_entries": 10451,
  "offset": 3,
  "total_pages": 3484,
  "current_page": 2,
  "per_page": 3,
  "data": [
    {
      "id": 6633,
      "created_at": "2013-01-29T14:55:36+01:00",
      "updated_at": "2016-01-06T10:27:10+01:00",
      "latitude": 52.4986,
      "longitude": 13.3918,
      "street": "",
      "zip": "",
      "city": "Berlin-Kreuzberg",
      "country": "Deutschland",
      "title": "wellcome-Ehrenamtliche für Berlin-Kreuzberg",
      "description": "Wir suchen Freiwillige, die Freude und Erfahrung im Umgang mit Säuglingen und Kleinkindern sowie Lust haben, junge Familien zu unterstützen. Als wellcome-Ehrenamtliche unterstützen sie Familien mit Kindern im 1. Lebensjahr individuell und alltagspraktisch. Für einen Zeitraum von ca. 3-5 Monaten besuchen sie \"ihre Familie\" ca. 1-2 mal wöchentlich und helfen die neue Situation zu meistern. wellcome-Ehrenamtliche fahren beispielsweise den Säugling spazieren, damit die Mutter ausruhen kann, sie begleiten die Zwillingsmutter zum Kinderarzt, holen das Geschwisterkind von der Kita ab oder sind einfach da und hören zu.\r\nNach einem Kennlerngespräch mit der wellcome-Koordinatorin erhalten die Ehrenamtlichen fachliche Begleitung, Fortbildungen und Möglichkeiten des Austauschs im Rahmen reegelmäßiger Ehrenamtstreffen. Die anfallenden Fahrtkosten werden erstattet und es besteht Versicherungsschutz.",
      "carrier": {
        "latitude": 52.53200149536133,
        "longitude": 13.43490028381348,
        "name": "wellcome in Berlin",
        "street": "Liselotte-Herrmann-Str. 33",
        "city": "Berlin",
        "zip": "10407",
        "country": "Deutschland",
        "links": [
          {
            "rel": "logo",
            "href": ""
          }
        ]
      },
      "vacancies": 10,
      "image": {
        "description": "wellcome-Ehrenamtliche im Einsatz",
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/fill_618x322_well_Ehrenamtliche.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/fill_270x141_well_Ehrenamtliche.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/well_Ehrenamtliche.jpg"
          },
          {
            "rel": "thumb",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/thumb_well_Ehrenamtliche.jpg"
          },
          {
            "rel": "medium",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/medium_well_Ehrenamtliche.jpg"
          },
          {
            "rel": "regular",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/regular_well_Ehrenamtliche.jpg"
          }
        ]
      },
      "contact": {
        "name": "Canan  Gerner",
        "phone": "030/ 32 53 23 42",
        "email": "berlin.kreuzberg@wellcome-online.de",
        "picture": null,
        "links": [

        ]
      },
      "topics": [
        "Nachbarschaft",
        "Kinder & Jugendliche"
      ],
      "activities": [
        "besuchen/begleiten",
        "pflegen/betreuen"
      ],
      "imported_from": null,
      "import_information": null,
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/fill_960x500_well_Ehrenamtliche.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/fill_730x380_well_Ehrenamtliche.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/fill_618x322_well_Ehrenamtliche.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/fill_410x214_well_Ehrenamtliche.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/fill_270x141_well_Ehrenamtliche.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/006/633/crop_original_well_Ehrenamtliche.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/6633.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/6633-wellcome-ehrenamtliche-fur-berlin-kreuzberg"
        }
      ]
    },
    {
      "id": 6775,
      "created_at": "2013-02-10T15:48:45+01:00",
      "updated_at": "2015-10-27T15:10:27+01:00",
      "latitude": 0.945,
      "longitude": 33.125,
      "street": "kiyunga mbulamuti kamuli road",
      "zip": "256",
      "city": "kamuli",
      "country": "Uganda",
      "title": "Give the children ideas,knowledge and support to become responsible citizens",
      "description": "The opportunity of the volunteers is guiding and counseling the community and teaching the young generation on how to behave in the orphanage life they are in.\r\nThe volunteers are required to pay for their transport to kiyunga in kisozi sub county in kamuli district.\r\nThe organization offers accommodation, feeding and some others the organization can afford.They willbe secured by the organization.for more inquiry  contact this(caomera@gmail.com)",
      "carrier": {
        "latitude": 0.9386024,
        "longitude": 33.1197774,
        "name": "Children's Hope Uganda",
        "street": "nawanyago-kisozi-kamuli road",
        "city": "kamuli",
        "zip": "+256",
        "country": "Uganda",
        "links": [
          {
            "rel": "logo",
            "href": ""
          }
        ]
      },
      "vacancies": 5,
      "image": {
        "description": "",
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "thumb",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/thumb_default.betterplace.png"
          },
          {
            "rel": "medium",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/medium_default.betterplace.png"
          },
          {
            "rel": "regular",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/regular_default.betterplace.png"
          }
        ]
      },
      "contact": {
        "name": "Kawomera David",
        "phone": "+256779996702",
        "email": "caomera@gmail.com",
        "picture": null,
        "links": [

        ]
      },
      "topics": [
        "Bildung",
        "Kinder & Jugendliche"
      ],
      "activities": [
        "beraten/coachen",
        "besuchen/begleiten",
        "organisieren/planen",
        "pflegen/betreuen"
      ],
      "imported_from": null,
      "import_information": null,
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_960x500_default.betterplace.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_410x214_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/crop_original_default.betterplace.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/6775.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/6775-give-the-children-ideas-knowledge-and-support-to-become-responsible-citizens"
        }
      ]
    },
    {
      "id": 6776,
      "created_at": "2013-02-10T15:49:29+01:00",
      "updated_at": "2015-10-28T16:45:59+01:00",
      "latitude": 0.945,
      "longitude": 33.125,
      "street": "kiyunga mbulamuti kamuli road",
      "zip": "256",
      "city": "kamuli",
      "country": "Uganda",
      "title": "Give the children ideas,knowledge and support to become responsible citizens",
      "description": "The opportunity of the volunteers is guiding and counseling the community and teaching the young generation on how to behave in the orphanage life they are in.\r\nThe volunteers are required to pay for their transport to kiyunga in kisozi sub county in kamuli district.\r\nThe organization offers accommodation, feeding and some others the organization can afford.They willbe secured by the organization.for more inquiry  contact this(caomera@gmail.com)",
      "carrier": {
        "latitude": 0.9386024,
        "longitude": 33.1197774,
        "name": "Children's Hope Uganda",
        "street": "nawanyago-kisozi-kamuli road",
        "city": "kamuli",
        "zip": "+256",
        "country": "Uganda",
        "links": [
          {
            "rel": "logo",
            "href": ""
          }
        ]
      },
      "vacancies": 5,
      "image": {
        "description": null,
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "thumb",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/thumb_default.betterplace.png"
          },
          {
            "rel": "medium",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/medium_default.betterplace.png"
          },
          {
            "rel": "regular",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/regular_default.betterplace.png"
          }
        ]
      },
      "contact": {
        "name": "Kawomera David",
        "phone": "+256779996702",
        "email": "caomera@gmail.com",
        "picture": null,
        "links": [

        ]
      },
      "topics": [
        "Bildung",
        "Kinder & Jugendliche"
      ],
      "activities": [
        "beraten/coachen",
        "besuchen/begleiten",
        "organisieren/planen",
        "pflegen/betreuen"
      ],
      "imported_from": null,
      "import_information": null,
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_960x500_default.betterplace.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_410x214_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/crop_original_default.betterplace.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/6776.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/6776-give-the-children-ideas-knowledge-and-support-to-become-responsible-citizens"
        }
      ]
    }
  ]
}
```

