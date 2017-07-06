
# Client Forwarding Request Status Page ⇄ [List](client_forwarding_requests_list.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/clients/some_client/forwarding_requests/1337.json
```

**For [betterplace.org clients](../README.md#client-api) only:**

After submitting a forwarding request, you can request a status of the asynchronous
forwarding job. It returns a JSON response, containing information about its status,
including failure reasons in the case of a failure.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">client_id</th>
    <td><code>some_client</code></td>
    <td>yes</td>
<td>

The betterplace.org-internal client permalink.

</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>1337</code></td>
    <td>yes</td>
<td>

          The ID of the forwarding request, normally returned within the
          response of a successful forwarding request POST.


</td>
  </tr>
</table>


## Response Attributes

  <th colspan="4">No response example defined</th>
</table>

## Response Links

<table>
  <tr>
    <th>Linkname</th>
    <th>Description</th>
  </tr>
  <th colspan="2">No response example defined</th>
</table>

## Response Example

```json
null
```

