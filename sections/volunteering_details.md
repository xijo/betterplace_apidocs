
# Volunteering Details ⇄ [List](volunteering_list.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/volunteering/28428.json
```

The details of a betterplace.org volunteering offer (donate time).

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
    <th align="left">id</th>
    <td><code>28428</code></td>
    <td>yes</td>
    <td>Volunteering-id as an integer number ≥ 1.</td>
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
  "id": 28428,
  "created_at": "2015-11-04T18:07:48+01:00",
  "updated_at": "2016-01-07T17:19:36+01:00",
  "latitude": 53.6815,
  "longitude": 9.98472,
  "street": "Ochsenzoller Straße 134",
  "zip": "22848",
  "city": "Norderstedt",
  "country": "Deutschland",
  "title": "SOS - Public Relation - Texter - Pressesprecher gesucht",
  "description": "SOS und Hilfe,\r\n\r\nwir kümmern uns um Kinder mit und ohne Migrantionshintergrund.\r\nDarin sind wir gut - sehr gut sogar, wenn man den Eltern Glauben schenken kann.\r\n\r\nWir sind aber auch ein Paria unter den Kindergärten dieser Welt und schwimmen gegen den Strom (gegen den Strom der Obrigkeit, nicht den der Kinder und Eltern!).\r\n\r\nWir starten gerade mehrere Aktionen in der Öffentlichkeit und brauchen dringend proffesionelle Hilfe und Unterstützung in Sachen PR.\r\nSelbstverständlich ist jegliche Tätigkeit im Zusammenhang mit dem gemeinnützigen Verein versichert.",
  "carrier": {
    "latitude": 53.6815137,
    "longitude": 9.98471559999996,
    "name": "Musischer Jugendkreis Norderstedt e.V.",
    "street": "Ochsenzoller Straße 134",
    "city": "Norderstedt",
    "zip": "22848",
    "country": "Deutschland",
    "links": [
      {
        "rel": "logo",
        "href": ""
      }
    ]
  },
  "vacancies": 1,
  "image": {
    "description": "Die KIDS brauchen uns und vor allem Dich",
    "links": [
      {
        "rel": "fill_618x322",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/fill_618x322_Gruppenbild_.jpg"
      },
      {
        "rel": "fill_270x141",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/fill_270x141_Gruppenbild_.jpg"
      },
      {
        "rel": "original",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/Gruppenbild_.jpg"
      },
      {
        "rel": "thumb",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/thumb_Gruppenbild_.jpg"
      },
      {
        "rel": "medium",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/medium_Gruppenbild_.jpg"
      },
      {
        "rel": "regular",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/regular_Gruppenbild_.jpg"
      }
    ]
  },
  "contact": {
    "name": "Ulrich Eidecker",
    "phone": "040-523 23 81",
    "email": "eidecker@focus-success.de",
    "picture": null,
    "links": [

    ]
  },
  "topics": [
    "Bildung",
    "Kinder & Jugendliche",
    "Flüchtlinge & Migranten",
    "Sozial Benachteiligte"
  ],
  "activities": [
    "PR / Social Media"
  ],
  "imported_from": null,
  "import_information": null,
  "profile_picture": {
    "fallback": true,
    "links": [
      {
        "rel": "fill_960x500",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/fill_960x500_Gruppenbild_.jpg"
      },
      {
        "rel": "fill_730x380",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/fill_730x380_Gruppenbild_.jpg"
      },
      {
        "rel": "fill_618x322",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/fill_618x322_Gruppenbild_.jpg"
      },
      {
        "rel": "fill_410x214",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/fill_410x214_Gruppenbild_.jpg"
      },
      {
        "rel": "fill_270x141",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/fill_270x141_Gruppenbild_.jpg"
      },
      {
        "rel": "original",
        "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/028/428/crop_original_Gruppenbild_.jpg"
      }
    ]
  },
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/volunteering/28428.json"
    },
    {
      "rel": "platform",
      "href": "https://www.betterplace.org/de/volunteering/28428-sos-public-relation-texter-pressesprecher-gesucht"
    }
  ]
}
```

