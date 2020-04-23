# Splunk Add-on for Microsoft Cloud Services

<table>
  <tr>
    <th>Input</th>
    <th>API</th>
    <th>Permissions</th>
    <th>Subscription Role (IAM)</th>
    <th>Notes</th>
  </tr>
  <tr>
    <td>Azure Storage Table</td>
    <td>N/A</td>
    <td>Access key OR Shared Access Signature: 
      <ul>
        <li> Allowed services: Blob, Table
        <li> Allowed resource types: Service, Container, Object
        <li> Allowed permissions: Read, List
      </ul>
    </td>
    <td>N/A</td>
    <td><a href="https://docs.microsoft.com/en-us/rest/api/storageservices/Constructing-an-Account-SAS" target="_blank">https://docs.microsoft.com/en-us/rest/api/storageservices/Constructing-an-Account-SAS</a>
  </tr>
</table>
