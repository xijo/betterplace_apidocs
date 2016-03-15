
# Project Blog Posts List ⇄ [Details](blog_post_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/projects/1114/blog_posts.json
```

A list of betterplace.org projects blog posts.
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**

* _Project-Blogposts:_ There is no client-scoped-url.
Please use the api calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.

* _All Blogposts:_ Clients can retrieve a list of all blogpost of all client-projects:
`/clients/PERMALINK/blog_posts.json`


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
    <td>Project-id as an integer number ≥ 14.</td>
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
      <th align="left">lang</th>
      <td>string</td>
      <td>en</td>
      <td>Blog posts have only one language at the moments</td>
    </tr>
    <tr>
      <th align="left">type</th>
      <td>string</td>
      <td>BlogPost</td>
      <td>Blogposts are always created by a user, and this
field always has the value <code>BlogPost</code>.
</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td>string</td>
      <td>Thank you from Beijing</td>
      <td></td>
    </tr>
    <tr>
      <th align="left">body</th>
      <td>string</td>
      <td>I am so happy to hear about the first donation for the Good Gifted Garden. If I told Chun …</td>
      <td>The body has html like links, embeded videos, pictures.</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="payout-ref" href="#payout">
            ↓payout
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td></td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="author-ref" href="#author">
            ↓author
          </a>
        </th>
      <td>string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke"
</td>
    </tr>
  </table>
### <a id="payout" href="#payout-ref">↑Nested Attributes: payout</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="payout.needs-ref" href="#payout.needs">
            ↓payout.needs
          </a>
        </th>
      <td>array</td>
      <td>TODO</td>
      <td>TODO</td>
    </tr>
  </table>
### <a id="payout.needs" href="#payout.needs-ref">↑Nested Attributes: payout.needs</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">payout.needs.need_title</th>
      <td>string</td>
      <td>Schoolbooks</td>
      <td>Title of the need</td>
    </tr>
    <tr>
      <th align="left">payout.needs.payout_amount_in_cents</th>
      <td>string</td>
      <td>2300</td>
      <td>Amount paid out to that need</td>
    </tr>
  </table>
### <a id="author" href="#author-ref">↑Nested Attributes: author</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">author.name</th>
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
          <a id="author.picture-ref" href="#author.picture">
            ↓author.picture
          </a>
        </th>
      <td>string</td>
      <td>//asset1.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</td>
      <td>User profile picture or a fallback image</td>
    </tr>
  </table>
### <a id="author.picture" href="#author.picture-ref">↑Nested Attributes: author.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">author.picture.fallback</th>
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
(<a href="blog_post_details.md">blog post details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">documentation</th>
      <td>Link to this resource in the documentation
</td>
    </tr>
    <tr>
      <th align="left">author.platform</th>
      <td>The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.
</td>
    </tr>
    <tr>
      <th align="left">author.contact_data</th>
      <td>The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.
</td>
    </tr>
    <tr>
      <th align="left">author.picture.fill_100x100</th>
      <td>100×100 Pixel</td>
    </tr>
    <tr>
      <th align="left">author.picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 92,
  "offset": 0,
  "total_pages": 46,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 74128,
      "created_at": "2012-11-28T10:27:50+01:00",
      "updated_at": "2012-11-28T10:27:50+01:00",
      "lang": "de",
      "type": "BlogPost",
      "title": "Skateistan in der ARD-Sendung \"Weltbilder\"",
      "body": "<p>Die ARD-Sendung Weltbilder besch&auml;ftigt sich mit der Lage der Kinder in Afghanistan. Der Fokus des Beitrags liegt dabei auf den Skateistan-Sch&uuml;lern <span>Khorshid und Parwana, die bei dem Selbstmord-Anschlag in der N&auml;he des ISAF-Hauptquartier Anfang September ums Leben kamen. Skateistan-Gr&uuml;nder Oli Percovich erkl&auml;rt in einem kurzen Interview, warum es wichtig ist, dass das Projekt weitergeht.</span></p>\r\n<p><span>Eine k&uuml;rzere Version des Beitrags zusammen mit einem Interview mit Rudi Tarneden von UNICEF Deutschland findet sich in der Tagesschau-Mediathek:</span></p>\r\n<p><a href=\"http://www.tagesschau.de/multimedia/video/video1218890.html\" target=\"_blank\">http://www.tagesschau.de/multimedia/video/video1218890.html</a></p>\r\n<p>Eine etwas l&auml;ngere Version gibt es in der Mediathek des NDR:</p>\r\n<p><a href=\"http://www.ndr.de/mediathek/index.html?media=weltbilder2659\" target=\"_blank\">http://www.ndr.de/mediathek/index.html?media=weltbilder2659</a></p>",
      "payout": null,
      "author": {
        "name": "E. Kinast",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/130/618/fill_100x100_original_Picture_023.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/130/618/crop_original_original_Picture_023.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/erika_k2"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/130618/contact_data.json"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/blog_posts/74128.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/1114-skateistan-afghanistan/news/74128"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
        }
      ]
    },
    {
      "id": 49498,
      "created_at": "2011-11-24T09:58:42+01:00",
      "updated_at": "2011-11-24T09:58:42+01:00",
      "lang": "en",
      "type": "BlogPost",
      "title": "Young Skateistan volunteer wins UNESCO drawing contest",
      "body": "<p>Skateistan students recently took part in a United Nations Educational, Scientific and Cultural Organisation (UNESCO) and United Nations Girls&rsquo; Education Initiative (UNGEI) drawing contest to promote the importance of gender equality in education.</p>\r\n<p>This semester at Skateistan our curriculum is all about the arts, so the drawing contest was a perfect opportunity to explore how we can express ourselves visually. Each class had discussions about equality in education before starting the drawings back in September.</p>\r\n<p>The winners were recently announced on the UNESCO website and one of our very own students, Hamdullah, was selected as a contest winner alongside other young artists from as far away as Bhutan, Timor and Mongolia. His drawing will be published in the UNGEI 2012 calendar.</p>\r\n<p>According to UNGEI, \"More than 3,000 drawings were received from 24 countries illustrating how gender equality in education benefits everyone. The aim of the contest and of the calendar is to raise public awareness on regional issues of gender equality in education, and to paint a picture of the benefits reaped from gender equality in education for both girls and boys.\"</p>\r\n<p>Hamdullah first came to Skateistan as a student, but has since become a volunteer, helping to teach and translate in workshops. He is also one of the star students in our advanced film-making classes. Keep it up Hamdullah, we are all proud of you!</p>\r\n<p>Check out the drawing&nbsp;<a href=\"http://skateistan.org/skateistan_blog/young-volunteer-wins-unesco-drawing-contest\" title=\"\" target=\"_blank\">here</a>.</p>",
      "payout": null,
      "author": {
        "name": "M. Henninger",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/009/238/fill_100x100_original_maxn_skate.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/009/238/crop_original_original_maxn_skate.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/max_h2"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/9238/contact_data.json"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/blog_posts/49498.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/1114-skateistan-afghanistan/news/49498"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
        }
      ]
    }
  ]
}
```

