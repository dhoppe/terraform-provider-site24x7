---
layout: "site24x7"
page_title: "Site24x7: site24x7_website_monitor"
sidebar_current: "docs-site24x7-resource-website-monitor"
description: |-
  Create and manage a Website monitor in Site24x7.
---

# Resource: site24x7\_website\_monitor

Use this resource to create, update and delete a website monitor in Site24x7.

## Example Usage

```hcl

// Website Monitor API doc: https://www.site24x7.com/help/api/#website
resource "site24x7_website_monitor" "website_monitor" {
  // (Required) Display name for the monitor
  display_name = "mymonitor"

  // (Required) Website address to monitor.
  website = "https://foo.bar"

  // (Optional) Check interval for monitoring. Default: 1. See
  // https://www.site24x7.com/help/api/#check-interval for all supported
  // values.
  check_frequency = "1"

  // (Optional) Authentication user name to access the website.
  auth_user = "theuser"

  // (Optional) Authentication password to access the website.
  auth_pass = "thepasswd"

  //(Optional) Credential Profile to associate the website with 
  credential_profile_id = "123"

  // (Optional) Check for the keyword in the website response.
  matching_keyword_value = "foo"

  // (Optional) Alert type to match on. See
  // https://www.site24x7.com/help/api/#alert-type-constants for available
  // values.
  matching_keyword_severity = 2

  // (Optional) Check for non existence of keyword in the website response.
  unmatching_keyword_value = "error"

  // (Optional) Alert type to match on. See
  // https://www.site24x7.com/help/api/#alert-type-constants for available
  // values.
  unmatching_keyword_severity = 2

  // (Optional) Match the regular expression in the website response.
  match_regex_value = ".*imprint.*"

  // (Optional) Alert type to match on. See
  // https://www.site24x7.com/help/api/#alert-type-constants for available
  // values.
  match_regex_severity = 2

  // (Optional) Perform case sensitive keyword search or not. Default: false.
  match_case = true

  // (Optional) User Agent to be used while monitoring the website.
  user_agent = "some user agent string"

  // (Optional) Timeout for connecting to website. Range 1 - 45. Default: 10
  timeout = 10

  // (Optional) Location Profile to be associated with the monitor. If 
  // location_profile_id and location_profile_name are omitted,
  // the first profile returned by the /api/location_profiles endpoint
  // (https://www.site24x7.com/help/api/#list-of-all-location-profiles) will be
  // used.
  location_profile_id = "123"

  // (Optional) Name of the Location Profile that has to be associated with the monitor. 
  // Either specify location_profile_id or location_profile_name.
  // If location_profile_id and location_profile_name are omitted,
  // the first profile returned by the /api/location_profiles endpoint
  // (https://www.site24x7.com/help/api/#list-of-all-location-profiles) will be
  // used.
  location_profile_name = "North America"

  // (Optional) Notification profile to be associated with the monitor. If
  // omitted, the first profile returned by the /api/notification_profiles
  // endpoint (https://www.site24x7.com/help/api/#list-notification-profiles)
  // will be used.
  notification_profile_id = "123"

  // (Optional) Name of the notification profile that has to be associated with the monitor.
  // Profile name matching works for both exact and partial match.
  // Either specify notification_profile_id or notification_profile_name.
  // If notification_profile_id and notification_profile_name are omitted,
  // the first profile returned by the /api/notification_profiles endpoint
  // (https://www.site24x7.com/help/api/#list-notification-profiles) will be
  // used.
  notification_profile_name = "Terraform Profile"

  // (Optional) Threshold profile to be associated with the monitor. If
  // omitted, the first profile returned by the /api/threshold_profiles
  // endpoint for the website monitor (https://www.site24x7.com/help/api/#list-threshold-profiles) will
  // be used.
  threshold_profile_id = "123"

  // (Optional) List of monitor group IDs to associate the monitor to.
  monitor_groups = [
    "123",
    "456"
  ]

  // (Optional) List of dependent resource IDs. Suppress alert when dependent monitor(s) is down.
  dependency_resource_ids = [
    "123",
    "456"
  ]

  // (Optional) List if user group IDs to be notified on down. 
  // Either specify user_group_ids or user_group_names. If omitted, the
  // first user group returned by the /api/user_groups endpoint
  // (https://www.site24x7.com/help/api/#list-of-all-user-groups) will be used.
  user_group_ids = [
    "123",
  ]

  // (Optional) List if user group names to be notified on down. 
  // Either specify user_group_ids or user_group_names. If omitted, the
  // first user group returned by the /api/user_groups endpoint
  // (https://www.site24x7.com/help/api/#list-of-all-user-groups) will be used.
  user_group_names = [
    "Terraform",
    "Network",
    "Admin",
  ]

  // (Optional) List if tag IDs to be associated to the monitor.
  tag_ids = [
    "123",
  ]

  // (Optional) List of tag names to be associated to the monitor. Tag name matching works for both exact and 
  //  partial match. Either specify tag_ids or tag_names.
  tag_names = [
    "Terraform",
    "Network",
  ]

  // (Optional) List of Third Party Service IDs to be associated to the monitor.
  third_party_service_ids = [
    "4567"
  ]

  // (Optional) Map of status to actions that should be performed on monitor
  // status changes. See
  // https://www.site24x7.com/help/api/#action-rule-constants for all available
  // status values.
  actions = {
    "1" = "123"
  }

  // (Optional) Resolve the IP address using Domain Name Server. Default: true.
  use_name_server = false

  // (Optional) Provide a comma-separated list of HTTP status codes that indicate a successful response. You can specify individual status codes, as well as ranges separated with a colon. Default: ""
  up_status_codes = "200,404"

  // (Optional) Enter true to follow up to 10 HTTP redirection responses or false not to follow HTTP redirections. Default value is true.
  follow_http_redirection = false

  // (Optional) Enter true or false to Trust the Server SSL Certificate. Default value is true.
  ignore_cert_err = true

  // (Optional) HTTP Method to be used for accessing the website. Default value is 'G'. 'G' denotes GET, 'P' denotes POST and 'H' denotes HEAD. PUT, PATCH and DELETE are not supported.
  // See https://www.site24x7.com/help/api/#http_methods for allowed values.
  http_method = "P"

  // (Optional) Provide content type for request params when http_method is 'P'. 'J' denotes JSON, 'T' denotes TEXT, 'X' denotes XML and 'F' denotes FORM
  request_content_type = "J"

  // (Optional) Provide the content to be passed in the request body while accessing the website.
  request_body = "{\"user_name\":\"joe\"}"
  
  // (Optional) Map of custom HTTP headers to send.
  request_headers = {
    "Accept" = "application/json"
  }

  // (Optional) Map of HTTP response headers to check.
  response_headers_severity = 0 // Can take values 0 or 2. '0' denotes Down and '2' denotes Trouble.
  response_headers = {
    "Content-Encoding" = "gzip"
    "Connection" = "Keep-Alive"
  }
}

```

## Attributes Reference

### Required

* `display_name` (String) Display Name for the monitor.
* `website` (String) Website address to monitor.

### Optional

* `id` (String) The ID of this resource.
* `check_frequency` (String) Interval at which your website has to be monitored. Default value is 1 minute.
* `timeout` (Number) Timeout for connecting to website. Default value is 10. Range 1 - 45.
* `use_ipv6`[Deprecated] (Boolean) Monitoring is performed over IPv6 from supported locations. IPv6 locations do not fall back to IPv4 on failure.
* `ip_type` (Number) Monitoring is performed over the selected internet protocol. Default value is 0. '0' -  Monitoring is performed over IPv4 from supported locations, '1' - Monitoring is performed over IPv6 from supported locations, '2' - IPv4 or IPv6 option will help in flexibly switching to the protocol that is supported in a particular location if one protocol fails, '3' - IPv4 and IPv6 will create two connections for each protocol. 
* `primary_protocol` (Number) Choose the primary internet protocol for the resources. Select only if you're choosing the option, Both IPv4 and IPv6 monitoring. '0' - IPv4, '1' - IPv6.
* `secondary_protocol_severity` (Number) Configure the change for the secondary resource for which you'd like to get notifications. Select only if you're choosing the option,Both IPv4 and IPv6 monitoring.​ '2' - Trouble. '3' - Critical.
* `hidden_mon_added` (Number) To Edit the existing secondary protocol resource.Select only if you are updating the option Both IPv6 and IPv4 monitoring or downgrading from Both IPv4 and IPv6 options to others but Not selected if you are choosing both IPv4 and IPv6 for the first time
* `matching_keyword_value` (String) Check for the keyword in the website response.
* `matching_keyword_severity` (Number) Severity with which alert has to raised when the matching keyword is found in the website response.
* `unmatching_keyword_value` (String) Check for the absence of the keyword in the website response.
* `unmatching_keyword_severity` (Number) Severity with which alert has to raised when the keyword is not present in the website response.
* `match_case` (Boolean) Perform case sensitive keyword search or not.
* `match_regex_value` (String) Match the regular expression in the website response.
* `match_regex_severity` (Number) Severity with which alert has to raised when the matching regex is found in the website response.
* `response_headers` (Map of String) A Map of response header name and value.
* `response_headers_severity` (Number) Severity with which alert has to raised when the header is found in the website response. Default value is 2. '0' denotes Down and '2' denotes Trouble.
* `http_method` (String) HTTP Method to be used for accessing the website. Default value is 'G'. 'G' denotes GET, 'P' denotes POST and 'H' denotes HEAD. PUT, PATCH and DELETE are not supported.
* `request_content_type` (String) Provide content type for request params when http_method is 'P'. 'J' denotes JSON, 'T' denotes TEXT, 'X' denotes XML and 'F' denotes FORM.
* `request_body` (String) Provide the content to be passed in the request body while accessing the website.
* `request_headers` (Map of String) A Map of request header name and value.
* `user_agent` (String) User Agent to be used while monitoring the website.
* `auth_method` (String) Authentication method to access the website. Default value is 'B'. 'B' denotes Basic/NTLM. 'O' denotes OAuth 2 and 'W' denotes Web Token.
* `auth_pass` (String) Authentication password to access the website.
* `auth_user` (String) Authentication user name to access the website.
* `credential_profile_id` (String)Credential Profile to associate the website with. Notes: If you're using Auth user and Auth password, you can't configure Credential Profile
* `client_certificate_password` (String) Password of the client certificate.
* `use_name_server` (Boolean) Resolve the IP address using Domain Name Server.
* `forced_ips` (String) Provide the domain name or IP addresses to be used for monitoring instead of using the IPs resolved from the given URL.
* `up_status_codes` (String) Provide a comma-separated list of HTTP status codes that indicate a successful response. You can specify individual status codes, as well as ranges separated with a colon.
* `follow_http_redirection` (Boolean) Enter true to follow up to 10 HTTP redirection responses or false not to follow HTTP redirections. Default value is true.
* `ignore_cert_err` (Boolean) Enter true or false to Trust the Server SSL Certificate. Default value is true.
* `ssl_protocol` (String) Specify the version of the SSL protocol. If you are not sure about the version, use Auto.
* `http_protocol` (String) Specify the version of the HTTP protocol. Default value is H1.1.
* `use_alpn` (Boolean) Enable ALPN to send supported protocols as part of the TLS handshake.
* `notification_profile_id` (String) Notification profile to be associated with the monitor. Either specify notification_profile_id or notification_profile_name. If notification_profile_id and notification_profile_name are omitted, the first profile returned by the /api/notification_profiles endpoint will be used.
* `notification_profile_name` (String) Name of the notification profile to be associated with the monitor. Profile name matching works for both exact and partial match.
* `threshold_profile_id` (String) Threshold profile to be associated with the monitor.
* `location_profile_id` (String) Location profile to be associated with the monitor.
* `location_profile_name` (String) Name of the location profile to be associated with the monitor.
* `monitor_groups` (List of String) List of monitor groups to which the monitor has to be associated.
* `dependency_resource_ids` (List of String) List of dependent resource IDs. Suppress alert when dependent monitor(s) is down.
* `user_group_ids` (List of String) List of user groups to be notified when the monitor is down. Either specify user_group_ids or user_group_names. If omitted, the first user group returned by the /api/user_groups endpoint will be used.
* `user_group_names` (List of String) List of user group names to be notified when the monitor is down. Either specify user_group_ids or user_group_names. If omitted, the first user group returned by the /api/user_groups endpoint will be used.
* `tag_ids` (List of String) List of tags IDs to be associated to the monitor. Either specify tag_ids or tag_names.
* `tag_names` (List of String) List of tag names to be associated to the monitor. Tag name matching works for both exact and partial match. Either specify tag_ids or tag_names.
* `third_party_service_ids` (List of String) List of Third Party Service IDs to be associated to the monitor.
* `actions` (Map of String) Action to be performed on monitor IT Automation templates. 


Refer [API documentation](https://www.site24x7.com/help/api/#website) for more information about attributes.
