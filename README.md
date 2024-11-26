# MetaSo

MetaSo is an open-source decentralized service package based on MetaID-v2 and MAN. It integrates fundamental on-chain MetaID social data, similar to Bitcoin nodes, making it easy for anyone to run a decentralized social node. Unlike Bitcoin nodes, MetaSo focuses solely on social data rather than transaction data.

# Base Protocols

### Public Social Protocols: simplebuzz/paylike/paycomment/simplerepost

**SimpleBuzz**

path: `/protocols/simplebuzz`

```json
{
    "content": "{Content}",
    "contentType": "{Content Format, default is text/plain}",
    "quotePin": "{Referenced/Quoted PinID}",
    "attachments": [
        "{metafile://PinID1}",
        "{metafile://PinID2}"
    ],
    "mention": [
        "{metaID1}",
        "{metaID2}"
    ]
}
```

**PayLike**

path: `/protocols/paylike`

```json
{
    "isLike": "1",
    "likeTo": "9bc429654d35a11e5dde0136e3466faa03507d7377769743fafa069e38580243i0"
}
```

**PayComment**

path: `/protocols/paycomment`

```json
{
	"content":"Nice comment",
	"commentTo":"c36feccf58b1a83c4df8a0b1517b74cf147509c1e25f4796ec493b1579a263f5i0",
	"replyTo":"", 
	"pay":"",
	"payTo": "",
}
```

**SimpleRepost**

path: `/protocols/simplerepost`

```json
{
	"rePostComment":"let me repost thisbuzz",
	"rePostTx:":"c36feccf58b1a83c4df8a0b1517b74cf147509c1e25f4796ec493b1579a263f5i0",
}
```

### Permission Protocols: PayBuzz/SubscribeBuzz/AccessControl/AccessPass

**PayBuzz**

path: `/protocols/paybuzz`

```json
{
    "publicContent": "{The public content}", // public preview part
    "encryptContent": "{Encrypted Content}", // encrypted content
    "contentType": "{Content Format, default is text/plain}",
    "publicFiles": [
		    "metafile://{pinid-1}", 
			  "metafile://{pinid-2}",
			  ...,
		],
    "encryptFiles": [
		    "metafile://{pinid-21}", 
		    "metafile://{pinid-22}",
		    ...,
		 ],
}
```

**SubscribeBuzz**

path: `/protocols/subscribebuzz`

```json
{
    "publicContent": "{The public content}", // public preview part
    "encryptContent": "{Encrypted Content}", // encrypted content
    "contentType": "{Content Format, default is text/plain}",
    "publicFiles": [
		    "metafile://{pinid-1}", 
			  "metafile://{pinid-2}",
			  ...,
		],
    "encryptFiles": [
		    "metafile://{pinid-21}", 
		    "metafile://{pinid-22}",
		    ...,
		 ],
}
```

**AccessControl**

path: `/metaaccess/accesscontrol`

```json
{
    "publicContent": "public part of content",//public part of content
	"publicPins":["PINID-1", "PINID-2"],//public pins
	"publicPath": "/protocols/simplepublicbuzz",//public path
	"controlPins":["PINID1","PINID2"], //Array of 'paybuzz' PINs that will be in control of accessing
	"controlPath": "/protocols/metaaccess/subscribebuzz",//The 'subscribebuzz' pins which is in this path will be in control of accessing
	"manDomain":"",//man domain
	"manPubkey":"THE-PUBKEY-OF-MAN", //Pubkey of the MAN node providing custody decryption services.
	"creatorPubkey":"THE-PUBKEY-OF-CREATOR",//Pubkey of the creator
	"encryptedKey":"Use the ECDH Key to Decrypt it and use that decryptedkey to decrypt the content",
	"holdCheck":{//hold check
		"type":"mrc20" //"chainCoin" or "mrc20", 
		"ticker":"mc" //the ticker of mrc20;if type = chainCoin then it will be ignored
		"amount":"1000"
	},
	"payCheck":{//pay check
		"type":"chainCoin", //"chainCoin" or "mrc20"
		"ticker":"",
		"amount":"0.00001",
		"payTo":"address",
		"validPeriod": "4320", //blocks，4320 means 1 month
	},
}
```

**AccessPass**

path: `/metaaccess/accesspass`

```json
{
	"accessControlID":"the-pinid-of-accesscontrol-file"
}
```

# Installation Guide

To make MetaSo accessible to everyone, all programs are packaged into a single installation package, including one-click upgrade handling, ensuring all MetaSo nodes across the network can stay in sync.

PS: If you need to view the tutorial on how to purchase a server, please refer to this tutorial.

## Quick Installation

1. Execute the following command on your server to start the installer:

    ```bash
    wget -qO- https://github.com/metaid-developers/metaso/releases/download/v0.1/installmetaso_boot.sh | sudo bash
    ```

    ![image.png](res/install/image-install-1.png)

    PS: If you need to delete and reinstall the installer, please refer to this tutorial.

2. Access the installer page at http://{server-IP}:7171 (port 7171 needs to be opened on your server)

    ![image.png](res/install/image-install-2.png)

   - Set initial password for installer security

   ![image.png](res/install/image-install-3.png)

   - Click "Install now" to proceed with installation

   ![image.png](res/install/image-install-4.png)

   - After installation is complete, you will see the following interface. If you see the 'Stop Service' button, it means that MetaSo is running normally and can be accessed. Click the 'Stop Service' button to stop MetaSo, and the 'Start service' button to start MetaSo.

   ![image.png](res/install/image-install-5.png)

3. Test the MetaSo service at http://{server-IP}:3000 (port 3000 needs to be opened)

    ![image.png](res/install/image-install-6.png)

4. Access admin settings at http://{server-IP}:3000/dashboardLogin

    ![image.png](res/install/image-install-7.png)

5. API documentation available at http://{server-IP}:7172 (Coming soon)

## Advanced Deployment

Coming soon

## Desktop Installation

Coming soon

## Upgrade Process

1. Visit http://{server-IP}:7171 to check current version against latest version
2. Click "Upgrade for latest" to perform the update
![image.png](res/upgrade/image-upgrade-1.png)

## Configuration

### Admin Account Setup
1. Modify `USERNAME` and `PASSWORD` in ./metaso/.env:
```
USERNAME=admin
PASSWORD=admin123456
```
2. Restart service through the installer page

### Additional Settings
- Customize appearance
![image.png](res/setting/image-setting-1.png)
- Set platform fees
![image.png](res/setting/image-setting-2.png)
- Configure blockchain RPC sources
![image.png](res/setting/image-setting-3.png)

## API Reference

**Common APIs:**
```
/social/buzz/newest         # Get latest buzz list
/social/buzz/hot           # Get trending buzz list
/social/buzz/info          # Get single buzz information
/social/buzz/interactive/info  # Get buzz interaction info
/social/user/info          # Get social information
```

## Troubleshooting

For common deployment issues and solutions, please refer to our [troubleshooting guide](link-to-troubleshooting).

## Security Notes

- Always secure your admin credentials
- Regularly update your installation
- Configure firewalls appropriately
- Back up your configuration files

## Contributing

We welcome contributions! Please see our contributing guidelines for more details.

## License

[License Information TBD]
