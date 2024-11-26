# MetaSo

MetaSo is an open-source decentralized service package based on MetaID-v2 and MAN. It integrates fundamental on-chain MetaID social data, similar to Bitcoin nodes, making it easy for anyone to run a decentralized social node. Unlike Bitcoin nodes, MetaSo focuses solely on social data rather than transaction data.

# Base Protocols

### Public Social Protocols: simplebuzz/paylike/paycomment/simplerepost

**simplebuzz**

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

**paylike**

path: `/protocols/paylike`

```json
{
    "isLike": "1",
    "likeTo": "9bc429654d35a11e5dde0136e3466faa03507d7377769743fafa069e38580243i0"
}
```

[Additional protocol definitions...]

# Installation Guide

To make MetaSo accessible to everyone, all programs are packaged into a single installation package, including one-click upgrade handling, ensuring all MetaSo nodes across the network can stay in sync.

PS: If you need to view the tutorial on how to purchase a server, please refer to this tutorial.

## Quick Installation

1. Execute the following command on your server to start the installer:
```bash
wget -qO- https://github.com/metaid-developers/man-indexer/releases/download/0.0.3/install_metaso_boot.sh | sudo bash
```
PS: If you need to delete and reinstall the installer, please refer to this tutorial.
![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/ee252e04-833f-401c-b159-6aadf18a5c31/image.png)

2. Access the installer page at http://{server-IP}:7171 (port 7171 needs to be opened on your server)
![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/cfe31315-6c4d-4c2d-bc81-19c2ade745ec/image.png)
   - Set initial password for installer security
   ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/cfe31315-6c4d-4c2d-bc81-19c2ade745ec/image.png)
   - Click "Install now" to proceed with installation
   ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/cfe31315-6c4d-4c2d-bc81-19c2ade745ec/image.png)
   - After installation is complete, you will see the following interface. If you see the 'Stop Service' button, it means that MetaSo is running normally and can be accessed. Click the 'Stop Service' button to stop MetaSo, and the 'Start service' button to start MetaSo.
   ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/cfe31315-6c4d-4c2d-bc81-19c2ade745ec/image.png)

3. Test the MetaSo service at http://{server-IP}:3000 (port 3000 needs to be opened)
![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/9afef87b-43b3-4244-8b32-673779e364b2/image.png)

4. Access admin settings at http://{server-IP}:3000/dashboardLogin
![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/48c14e7c-3756-44f8-afd1-6da4d1465cec/image.png)

5. API documentation available at http://{server-IP}:7172 (Coming soon)

## Advanced Deployment

TBD

## Desktop Installation

TBD

## Upgrade Process

1. Visit http://{server-IP}:7171 to check current version against latest version
2. Click "Upgrade for latest" to perform the update
![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/29f70d94-8dc0-4aa8-bb83-99c1617989c5/image.png)

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
![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/731b7460-7ce3-4fcb-b0ef-5b3284355de4/image.png)
- Set platform fees
![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/abe961ca-068d-4ef3-bec3-6e5660ff6bc3/image.png)
- Configure blockchain RPC sources
![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c3f7aef2-7bc0-49bb-ac61-d785169ca624/bf79ee7d-ac0a-47af-84a2-ace18a0f3031/image.png)

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
