---
sidebar_position: 1
---

import Releases from "../releases.json";

# CompuTec AppEngine

:::caution
    After upgrade from any 1.00 version to any 2.00, please use the Empty Cache and Hard Reload option in the browser on which you use AppEngine.
:::

## Releases

<table>
  <tr>
    <th>Version</th>
    <th>Release Date</th>
    <th>Installer</th>
    <th>Minimal required related version</th>
  </tr>
  {Releases.map((data) => (
    <tr>
      <td>{data.version}</td>
      <td>{data.release_date}</td>
      <td><a href={`https://download.computec.one/software/appengine/releases/CompuTec_AppEngine_${data.build}_x64.exe`}>Download</a></td>
      <td>ProcessForce {data.pf_version}<br />CompuTec License Server {data.license_server_version}</td>
    </tr>
  ))}
</table>
