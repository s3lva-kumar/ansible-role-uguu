 ansible role uguu
===================

This role installs [uguu](https://github.com/nokonoko/Uguu). Uguu is a simple lightweight temporary file hosting and sharing platform, but can also be used as a permanent file host

## Sample example of use in a playbook

The following code has been tested with Ubuntu 20.04

```yaml
 
- name: "install uguu"
  hosts: enter your hosts file
  become: yes
  role:
    - ansible-role-uguu

  vars:
    git_release_version: v1.5.0
    max_upload_size: '128'
    paypalUrl: ""
    bitcoinAddress: ""
    siteName: name of your site
```
### Variables

These below variables are changeable. You can change these variables according to the description

| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `ubuntu_release` | `focal` | `Give your ubuntu release for add nginx repo` |
| `OnCalendar` | `*-*-* *:*:30` | `Define shell script running periodically. If change this shedule, give systemd OnCalendar time` |
| `uguu_release_version` | `v1.5.0` | `Give which release clone and install` |

### Front End
| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `max_upload_size` | `128` | `The max file size which an user can upload in MB` |
| `siteName` | `SITENAME` | `The name of your site. This will appear in the browser title and on several places on the website. If you changed the expire time remember to change that here as well` |
| `subTitle` | `whoo` | `site subtitle.` |
| `siteUrl` | `https://yoursite.com` | `Url to your site` |
| `abuseContact` | `abuse@example.com` | `The email dedicated to receive abuse reports, this can be the same as infoContact if you want. Make sure it's a valid email or else you run the risk of getting into trouble from your server provider` |
| `infoContact` | `info@example.com` | `The email dedicated to receive general email from users` |
| `ServerCountryLocation` | `Sweden` | `The country your server is located in, this is related to abuse/DMCA since it often depends on local laws` |
| `SiteMetaInfo` | `'{{ siteName }} is a temporary file hosting service, upload files up to 128MiB for24 hours'` | `A description of your site, search engines show this data in searches for your site` |

### Donations
| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `donationBanner` | `false` | `true/false depending if you want to compile the donation banner` |
| `paypalUrl` | `""` | `The URL to your Paypal donation page` |
| `bitcoinAddress` | `""` | `Your BTC address for donations` |
| `flattrUrl` | `""` | `Your Flattr donation URL` |
| `kofiUrl` | `""` | `your Ko-Fi donation URL. This can be ignored if the donations banner isn't enabled. or if you don't want to enable that method of donating.` |

### Database and Upload File Store path
| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `DB_PATH` | `'/var/www/db/uguu.sq3'` | `Path to your database` |
| `FILES_ROOT` | `'/var/www/files/'` | `The location where uploaded files are to be stored` |
| `FILE_URL` | `'{{ ansible_eth1.ipv4.address }}/files'` | `the URL of the subdomain serving the uploaded files, If you used single domain give that domain name or if you use localhost leave this default` |

### Misc
| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `malwareBanner` |  `"false"` | `true/false depending if you want to compile the malware banner.` |
| `LOG_IP` | `'false'` | `You want you can turn this on and the IP of the uploaded file will be stored in the DB` | 
| `ANTI_DUPE` | `'false'` | `If enabled a file already uploaded won't be uploaded again` |
| `FILES_RETRIES` | `'15'` | `maximum number of tries to regenerate filename in case an existing one already exists, this is highly unlikely and even if it does 15 tries is more than enough` |
| `NAME_LENGTH` | `'8'` | `The length of the new filename` |

## Contributing
Don't hesitate to create a pull request
