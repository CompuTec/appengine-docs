---
sidebar_position: 2
---

import Releases from "../processforce-releases.json";

# CompuTec ProcessForce Plugin

<table>
  <tr>
    <th>Version</th>
    <th>Build</th>
    <th>Release Date</th>
    <th>Package</th>
    <th>Minimal AppEngine Version</th>
    <th>This version works with</th>
  </tr>
  {Releases.map((data) => (
    <tr>
      <td>{data.version}</td>
      <td>{data.build}</td>
      <td>{data.release_date}</td>
      <td><a href={data.download_url}>Download</a></td>
      <td>{data.minimal_ae_version}</td>
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
