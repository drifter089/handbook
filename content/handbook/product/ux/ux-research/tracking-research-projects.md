---

title: "Tracking gold, silver, and bronze UX research projects"
description: "How we track research research projects, by service level."
---









As part of our [UX research prioritization](/handbook/product/ux/ux-research/research-prioritization/) process, each UX research project issue will have one of the following labels:

- `UX Research Prioritization: Gold`
- `UX Research Prioritization: Silver`
- `UX Research Prioritization: Bronze`

The labels are used to generate [this dashboard (internal only)](https://app.periscopedata.com/app/gitlab/1063612/UX-research-projects), which informs us of the following:

- Total number of new UX research projects opened each quarter, by service level
- Total number of new UX research projects opened each quarter, by stage
- Average number of days it takes to complete a UX research project by service level
- Total number of open UX research projects, by service level

Collectively, these data visualizations helps us understand more about the volume of UX research occurring, the lifecycle of a UX research project, and where UX research projects are taking place. 


<% if ENV['PERISCOPE_EMBED_API_KEY'] %>
  <div>
    <embed width="100%" height="400" src="<%= signed_periscope_url(chart: 15250081, dashboard: 1063612, embed: 'v2') %>">
  </div>
  <% else %>
    <p>You must set a <code>PERISCOPE_EMBED_API_KEY</code> environment variable to render this chart.</p>
<% end %>

<% if ENV['PERISCOPE_EMBED_API_KEY'] %>
  <div>
    <embed width="100%" height="400" src="<%= signed_periscope_url(chart: 15225364, dashboard: 1063612, embed: 'v2') %>">
  </div>
  <% else %>
    <p>You must set a <code>PERISCOPE_EMBED_API_KEY</code> environment variable to render this chart.</p>
<% end %>




