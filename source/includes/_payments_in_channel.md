# Payments in Channel

Funder/fundee create commitment transactions.


## sender creates a commitment transaction to pay

<!-- right -->
> Alice's data:

```shell
last_temp_pub_key：       n2gj8MDzUU7JZ6eVF5VpXcL4wUfaDXzTfJ
last_temp_private_key：  cSgTisoiZLzH5vrwHBMAXLC5nvND2ffcqqDtejMg12rEVrUMeP5R
curr_temp_address：       mpnHbpARXjUBcf6vib7E3jjD6Zv4CrvYuW
curr_temp_private_key： cP8vR19XbtytyHgyBh1SV5dVAMLrLR2rzSU9EAcQTCUHij61u5C2
curr_temp_pub_key: 02b8302d22a50fd84f34d528ff98998a6959bc7fb8f45b5f3fb44e23101aa5d8f2
```
 
> Alice creates a commitment transaction:

```shell
{
	"type":-351,
	"data":{
		"channel_id":[59,253,135,228,203,197,78,61,223,84,135,17,136,165,253,7,69,70,182,254,95,86,78,118,149,122,33,222,129,249,52,197],
		"amount":0.1,
		"curr_temp_address_pub_key":"02b8302d22a50fd84f34d528ff98998a6959bc7fb8f45b5f3fb44e23101aa5d8f2",
		"curr_temp_address_private_key":"cP8vR19XbtytyHgyBh1SV5dVAMLrLR2rzSU9EAcQTCUHij61u5C2",
		"property_id":121,
		"channel_address_private_key":"cUAdadTkjeVFsNz5ifhkETfAzk5PvhnLWtmdSKgbyTTjSCE4MYWy",
		"last_temp_address_private_key":"cSgTisoiZLzH5vrwHBMAXLC5nvND2ffcqqDtejMg12rEVrUMeP5R"
	}
}
```

> OBD Responses:

```json
{
	"type":-351,
	"status":true,
	"from":"alice",
	"to":"bob",
	"result":{
		"amount":0.1,
		"channel_address_private_key":"",
		"channel_id":[59,253,135,228,203,197,78,61,223,84,135,17,136,165,253,7,69,70,182,254,95,86,78,118,149,122,33,222,129,249,52,197],
		"curr_temp_address_private_key":"",
		"curr_temp_address_pub_key":"02b8302d22a50fd84f34d528ff98998a6959bc7fb8f45b5f3fb44e23101aa5d8f2",
		"last_temp_address_private_key":"",
		"property_id":121,
		"request_commitment_hash":"8a55f150c34e2720a587dde3809e81959701e1dd3f78c1e1fc9960c132566fe0"
	}
}
```

<!-- center -->

**Message Type: -351**
 
**Either funder or fundee sends:**

Parameter | default | placement | Description
--------- | ------- | --------- | ------------
channel_id         		| ------- |   data    | 
amount  			| ------- |   data    | amount to pay
curr_temp_address_pub_key       | ------- |   data    | temporary multi-sig address
curr_temp_address_private_key   | ------- |   data    | the private key of the temporary multi-sig address currently in use. 
property_id		   	| ------- |   data    | the omni asset id that has been funding.
channel_address_private_key     | ------- |   data    | Alice's private key of the channel
last_temp_address_private_key   | ------- |   data    | the private key of the last temporary multi-sig address


**OBD Responses:**

Parameter | default | placement | Description
--------- | ------- | --------- | ------------
status         | ------- |   body    | true or false
from	       | ------- |   body    | peer id of funder
to             | ------- |   body    | peer id of fundee
amount 	       | ------- |   result  | 
channel_address_private_key  		| ------- |   result    | 
channel_id 				| ------- |   result    | 
curr_temp_address_private_key 		| ------- |   result    | 
curr_temp_address_pub_key 		| ------- |   result    | 
last_temp_address_private_key 		| ------- |   result    | 
property_id 				| ------- |   result    | 
request_commitment_hash 		| ------- |   result    | 


## Receiever accepts the tokens

<!-- right -->
> Bob's data: 

```shell
last_temp_pub_key： 
last_temp_private_key： 
curr_temp_pub_key：       mt1jUkFb9JtR3qBeYHqJE68S6TUct7fB8r
curr_temp_private_key： cQm58g783uvXbFjTjLN5STR3TrPiKueC5f9SCkAc9kSew4dj2Y2i
curr_temp_pub_key：   0277bf9e0df3ffe2d8f22356fb198e9b0a2237b8c51bde77e3c7da5df09a4dba05
```

> Bob replies: 

 
```shell
 {
	"type":-352,
	"data":{
		"channel_id":[59,253,135,228,203,197,78,61,223,84,135,17,136,165,253,7,69,70,182,254,95,86,78,118,149,122,33,222,129,249,52,197],
		"curr_temp_address_pub_key":"0277bf9e0df3ffe2d8f22356fb198e9b0a2237b8c51bde77e3c7da5df09a4dba05",
		"curr_temp_address_private_key":"cQm58g783uvXbFjTjLN5STR3TrPiKueC5f9SCkAc9kSew4dj2Y2i",
		"last_temp_private_key":"",
		"request_commitment_hash":"8a55f150c34e2720a587dde3809e81959701e1dd3f78c1e1fc9960c132566fe0",
		"channel_address_private_key":"cV6dif91LHD8Czk8BTgvYZR3ipUrqyMDMtUXSWsThqpHaQJUuHKA",
		"approval":true
	}
}

```


> OBD Responses：

```json
{
	"type":-352,
	"status":true,
	"from":"bob",
	"to":"alice",
	"result":{
		"amount_b":0.1,
		"amount_m":5.9,"channel_id":[59,253,135,228,203,197,78,61,223,84,135,17,136,165,253,7,69,70,182,254,95,86,78,118,149,122,33,222,129,249,52,197],
		"create_at":"2019-09-21T01:38:02.249498+08:00",
		"create_by":"bob",
		"curr_hash":"235d465eae3bb8c71e97ca08cca295598461cc8d23a9bdf4e6ff09e4e9f9323f",
		"curr_state":10,
		"id":5,
		"input_amount":6,
		"input_txid":"c734f981de217a95764e565ffeb6464507fda588118754df3d4ec5cbe487fd3b",
		"input_vout":2,"last_commitment_tx_id":4,"last_edit_time":"2019-09-21T01:38:02.249498+08:00",
		"last_hash":"8a55f150c34e2720a587dde3809e81959701e1dd3f78c1e1fc9960c132566fe0",
		"multi_address":"2Mz8QZz1RxwpHioy1bgyPA4rhXXWwEkFDtW",
		"owner":"alice",
		"peer_id_a":"alice",
		"peer_id_b":"bob",
		"property_id":121,
		"redeem_script":"522102b8302d22a50fd84f34d528ff98998a6959bc7fb8f45b5f3fb44e23101aa5d8f22103efd8923f1829ece87202892d31cd75c20b7a7b5adf888f7ba04fa2c1bc931ce952ae",
		"script_pub_key":"a9144b7ecd257a459e0fabf75b72fdfd98a54a12e7c187",
		"send_at":"0001-01-01T00:00:00Z",
		"sign_at":"2019-09-21T01:38:03.119512+08:00",
		"temp_address_pub_key":"02b8302d22a50fd84f34d528ff98998a6959bc7fb8f45b5f3fb44e23101aa5d8f2",
		"transaction_sign_hex_to_other":"02000000043bfd87e4cbc54e3ddf54871188a5fd074546b6fe5f564e76957a21de81f934c702000000d900473044022068d84ef3d9d6db850d1c348ae52158ee542758ed4f82f1359a901999657ea8d902202e63d2c3e7ddba77b69fd6d71eee072964f9e0fd6972b11922ae64b4d4b5d7fa0147304402202903a8784eeb72dc7f32e048a50134f217a4b7ccf371066ddce2c7fafa863a9c0220117307e4e7efe7e74321707310e6a2c387e4a5002fd3bc654d1860275ee157e801475221021d475729c52f86df24b36aa231945bd090f9c23ccbfb91e4ade6813b2419d32d2103efd8923f1829ece87202892d31cd75c20b7a7b5adf888f7ba04fa2c1bc931ce952aeffffffff6aabc30d6ef0d7e1d02572ca30450421a7541b7bf3d9b9937240b977b228215c00000000d90047304402205536325b0b93f34528c4cb8d31f0f43c39bd035db521bc3dca54ae8a99accd0902203bd9ca2bce0ee8314f5a8998a0cb64a0edc17abe8f60ad813e0e41f1ddaf9bdc014730440220628681cd6a6fc23ce8074788ce13c7da998dc94af9fd9d1d0bbe8ad98f86ddbd02205c016cabce74eaf577b6702760129cd3f86173b6ffeb008cca7783240634dde901475221021d475729c52f86df24b36aa231945bd090f9c23ccbfb91e4ade6813b2419d32d2103efd8923f1829ece87202892d31cd75c20b7a7b5adf888f7ba04fa2c1bc931ce952aeffffffffd8f2a3c2a2b2e6678d21025aed46cbc905ba25ac55e0dfd50a2d719b687f1c5203000000d900473044022001e87986132f4f8ad3e4264044fecdd1afe813aeed1a540ff96f11c159774c0f022016b7cb615ae10e48d911b5fddf3e8770829e489f61971203e9462854c81b493a0147304402206e46182bf84fe5c4d1f7b5c78b80c315bb6a5f7922a6f33afa68cec3a84f79ad02205168f413d7345fbb1d22f7f2540588934e5851d2243c3ad03f6ac1e04ccf26d001475221021d475729c52f86df24b36aa231945bd090f9c23ccbfb91e4ade6813b2419d32d2103efd8923f1829ece87202892d31cd75c20b7a7b5adf888f7ba04fa2c1bc931ce952aeffffffffdea307c20723ced3445b67d801c2c28a7cc371092e9500dac8f96d5c892abba402000000d90047304402204586943539db1a9087b26678a7c6a20cadc38e2545d061ab8c2a25c245d817de02202f8bfb63e5448054be581ffffb64db1297ca95728bdf4be8f0b6ffff7107dbe8014730440220750202e5eef02556b22b124bc1bb2452918df7e02fb639e07432fc0e42829a4502204071fc1b6d60d3275b081920085777134547f4c986f15bbb5284989fc07d3ebb01475221021d475729c52f86df24b36aa231945bd090f9c23ccbfb91e4ade6813b2419d32d2103efd8923f1829ece87202892d31cd75c20b7a7b5adf888f7ba04fa2c1bc931ce952aeffffffff039a460000000000001976a914b5770ba3d6d34f5fdd8d582f81fb383975bb9c6d88ac0000000000000000166a146f6d6e690000000000000079000000000098968022020000000000001976a914c2e30e5f058df787de0529e0742d7ef7a13231ab88ac00000000","transaction_sign_hex_to_temp_multi_address":"0200000001685a7e84bc2d24fa01550674176a6b4bf366a99e001b5b52f2fc16c8b6146b2600000000d90047304402207fdf6d9de273352f215b7139a169b9c6046fc33f5e5c26a4012c6b32e07137aa02200a437ce51e3a02478c59d8c21a8c71ea6fda6dac62c5032ec5f131f21a7e8ee20147304402205eccc7e4b8bcae3269d6eb25aeb6823d88562f308c203590b86073d35f9d3d7e02203130cf67e48b539d7b3c17400a7fba88c812315f465a42dabab046d65a52054c01475221021d475729c52f86df24b36aa231945bd090f9c23ccbfb91e4ade6813b2419d32d2103efd8923f1829ece87202892d31cd75c20b7a7b5adf888f7ba04fa2c1bc931ce952aeffffffff033c1900000000000017a9144b7ecd257a459e0fabf75b72fdfd98a54a12e7c1870000000000000000166a146f6d6e69000000000000007900000000232aaf801c0200000000000017a9144b7ecd257a459e0fabf75b72fdfd98a54a12e7c18700000000","txid_to_other":"3065fa232bb5dec89104bc487359ac12b2480bb0762f64abbebd6adf0795bc13","txid_to_temp_multi_address":"74cffd8987cf01ed02d355aad82c38aadd991c4f185b3e394c5bade55d2ceb73"
	}
}

```


<!-- center -->

Receiever notify the sender that he has receieved the money. 

**Message Type: -352**
 
**Receiever sends**

Parameter | default | placement | Description
--------- | ------- | --------- | ------------
channel_id         			| ------- |   data    | 
curr_temp_address_pub_key               | ------- |   data    | to be added
curr_temp_address_private_key           | ------- |   data    | to be added
last_temp_private_key     		| ------- |   data    | to be added
request_commitment_hash			| ------- |   data    | to be added
channel_address_private_key 		| ------- |   data    | private key of the channel that Bob holds
approval

	 
 
**OBD Responses:**

Parameter | default | placement | Description
--------- | ------- | --------- | ------------
status           | ------- |   body    | true or false
from	         | ------- |   body    | peer id of funder
to               | ------- |   body    | peer id of fundee
amount_b         | ------- |   result  | how much has been payed
amount_m         | ------- |   result  | the balance of the sender 
channel_id       | ------- |   result  | channel officially created
create_at        | ------- |   result  | 
create_by        | ------- |   result  | created by the funder
curr_state       | ------- |   result  | 
id               | ------- |   result  | 
input_amount 	 | ------- |   result  | 
input_txid 	 | ------- |   result  | 
input_vout	 | ------- |   result  | 
last_commitment_tx_id 	| ------- |   result  | to be added
last_edit_time 		| ------- |   result  | 
last_hash 		| ------- |   result  | 
multi_address 		| ------- |   result  | to be added
owner 			| ------- |   result  | 
peer_id_a 		| ------- |   result  | 
peer_id_b 		| ------- |   result  | 
property_id 		| ------- |   result  | 
redeem_script 		| ------- |   result  | to be added
script_pub_key 		| ------- |   result  | to be added
send_at 		| ------- |   result  | 
sign_at 		| ------- |   result  | 
temp_address_pub_key 	| ------- |   result  | to be added
transaction_sign_hex_to_other 	| ------- |   result  | to be added
 

