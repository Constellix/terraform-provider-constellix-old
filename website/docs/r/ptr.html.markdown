---
layout: "constellix"
page_title: "CONSTELLIX: constellix_ptr_record"
sidebar_current: "docs-constellix-resource-constellix_ptr_record"
description: |-
  Manages records of type PTR  for a specific domain.
---

# constellix_ptr_record
Manages records of type PTR  for a specific domain.

## Example Usage ##

```hcl
resource "constellix_ptr_record" "ptr1" {
  domain_id   = "${constellix_domain.domain1.id}"
  source_type = "domains"
  name        = "pointer1"
  ttl         = "10"
  note        = "Practice record"
  noanswer    = false
  gtd_region  = 1
  type        = "PTR"
  roundrobin {
    value        = 13
    disable_flag = "true"
  }
}

```

## Argument Reference ##
* `source_type` - (Required) Type of the PTR record. The values which can be applied are "domains" or "templates".
* `name` - (Optional) Name of record. Name should be unique.
* `ttl` - (Required) TTL must be in between 0 and 2147483647.
* `noanswer` - (Optional) Shows if record is enabled or disabled. Default is false (Active).
* `note` - (Optional)Record note.
* `gtd_region` - (Optional) Shows id of GTD region in which record is to be created. 1 for World (Default). 2 for Europe. 3 for US East. 4 for US West. 5 for Asia Pacific. 6 for Oceania. note: "gtdRegion" from 2 to 6 will be applied only when GTD region is enabled on domain.
* `type` - (Optional) Record type A.
* `roundrobin` - (Required) Object.
* `roundrobin.value` - (Required) This will be the host name of the computer or server the IP resolves to, for example mail.example.com. It is important to note, the domain name is automatically appended to the end of this field unless it ends with a dot (.).
* `roundrobin.disable_flag` - (Optional) enable or disable the roundrobin object. Default is false. Atleast one roundrobin object should be false.

## Attributes Reference
The only attribute that this resource exports is the `id`, which is set to the constellix calculated id of the PTR resource.