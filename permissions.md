<table width=100%>
  <thead>
    <tr>
      <th>Add-on</th>
      <th>Input/Action</th>
      <th>API</th>
      <th>Permissions</th>
      <th>Role (IAM)</th>
      <th>Default Sourcetype(s) / Sources</th>
      <th>Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="3">Splunk Add-on for Microsoft Cloud Services</td>
    <td>Azure Storage Table <br/>
Azure Storage Blob</td>
      <td> N/A </td>
      <td>
        Access key  OR <br />
Shared Access Signature:
        <ul>
        <li>Allowed services: Blob, Table</li>
        <li>Allowed resource types: Service, Container, Object</li>
        <li>Allowed permissions: Read, List</li>
        </ul>
      </td>
      <td> N/A </td>
      <td>
        mscs:storage:blob <br />
mscs:storage:blob:json <br />
mscs:storage:blob:xml <br />
mscs:storage:table
      </td>
      <td><a href="https://docs.microsoft.com/en-us/rest/api/storageservices/Constructing-an-Account-SAS" target="_blank">https://docs.microsoft.com/en-us/rest/api/storageservices/Constructing-an-Account-SAS</a></td>
    </tr>
    <tr>
      <td>Azure Audit</td>
      <td> N/A </td>
      <td> N/A </td>
      <td> (Subscription) Reader </td>
      <td> mscs:azure:audit </td>
      <td></td>
    </tr>
    <tr>
      <td>Azure Resource</td>
      <td> N/A </td>
      <td> N/A </td>
      <td> (Subscription) Reader </td>
      <td>
        mscs:resource:virtualMachine <br />
mscs:resource:networkInterfaceCard <br />
mscs:resource:publicIPAddress <br />
mscs:resource:virtualNetwork <br />
mscs:resource:disk <br />
mscs:resource:image <br />
mscs:resource:snapshot <br />
mscs:resource:resourceGroup <br />
mscs:resource:subscriptions <br />
mscs:resource:security Group
      </td>
      <td></td>
    </tr>
  </tbody>
</table>
