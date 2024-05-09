---
sidebar_position: 15
---

import Releases from "../../serialization-releases.json";

# CompuTec Serialization Plugin

:::caution
    In order to use this plugin, you have to install the CompuTec ProcessForce plugin first.
:::

<table>
  <tr>
    <th>Version</th>
    <th>Build</th>
    <th>Release Date</th>
    <th>Package</th>
    <th>Minimal Requirements</th>
  </tr>
  {Releases.map((data) => (
    <tr>
      <td>{data.version}</td>
      <td>{data.build}</td>
      <td>{data.release_date}</td>
      <td><a href={data.download_url}>Download</a></td>
      <td>
        <ul>
            {data.requirements.map((requirement) => (
                <li>{requirement}</li>
            ))}
        </ul>
      </td>
    </tr>
  ))}
</table>
