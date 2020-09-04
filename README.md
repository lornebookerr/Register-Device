# Device Registry System
## This wil work with all of the other modules

### This follows a tutorial from Jake Wright
[Tutorial Link](https://www.youtube.com/watch?v=4T5Gnrmzjak&list=PLlj9BrHKq9WI4R30l_M_tdRMPF4AZ6dcs&index=2)

**Description**

This module registers all of the devices to be used by everything else
It is planned to use 'GET', 'POST' and 'DELETE'

## Usage

All responses will use the following format


``` json
{
	"data":"Content of the response",
	"message":"Description of what happened"
}
```

**What it does**

`GET /devices`

**Response**

- `200 OK` returned on success

``` json
[
	{
		"identifier":"desk-lamp",
		"name":"Desk Lamp",
		"device_type":"smart-plug",
		"controller-gateway":"KASA"
	}
	{
		"identifier":"apple-tv",
		"name":"Bedroom Apple TV",
		"type":"smart-box",
		"controller-gateway":"192.168.0.26"
	}
]
```

### Registering a new device

**What it does**

`POST /devices`

**Args**

- `"identifier":device-name`
- `"name":display-name`
- `"type":device_type`
- `"controller-gateway":ip-address`

If a new entry matches an existing device, it will be overwritten


**Response**

- `404 Not Found` if the device does not  exist
- `200 OK` on success

``` json
{
	"identifier":"desk-lamp",
	"name":"Desk lamp",
	"device_type": "smart-plug",
	"controller-gateway":"192.168.0.2"
}
```

## Delete a device

**Definition**

`DELETE /devices/<identifier>`

**Response**

- `404 Not Found` if the device not exist
- `204 No Content` on success