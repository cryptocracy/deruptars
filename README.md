# repo
Contains the layers for OG Deruptars NFTs, that are part of the Derupt Alpha at https://mia.derupt.io 

# premise
Derupt Alpha: OG "Deruptars" are NFTs used in Derupt Alpha, as Profile Avatars. 

Derupt Beta+: OG "Deruptars" are NFTs used in Derupt Beta and later, as Profile Avatars and or Badges (Badge Color Determined by Count Owned)

# how
The OG Deruptar Avatar NFT Images is the result of a compositing of layered png files.

We first got the first 4444 STX addresses per the Stacks Blockchain.

Cropped the first 4 Characters. (Trim the SP [or ST if testnet] + next 2 characters.)

Then concatenated the next 4 Characters of the string, with just the last 4 Characters of the string.

Once we had our 8 digit string we would use that to select the relative layers in the composite process.

The over all process went something like this per OG NFT.

Get 8 digit string
```
var depositaddress = "STXADDRESS"; //An STX address
var rawaddy = depositaddress.substring(4); //Crop first 4 digits
var a1 = rawaddy.substr(0,4); // keep next 4 digits
var z1 = rawaddy.substring(rawaddy.length - 4); //keep last 4 digits
msg.payload = a1+z1; // concat both and pass string along
return msg;
```
Then split 8 digit string into an array something looking like this.
```
{
   "payload":["A","8","4","J","A","R","7","M"]
}
```
Then pass in to composite via looking something like/
```
<div style="position: relative; width: 284px; height: 284px;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/bg/{{msg.payload[0]}}_bg.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/skin/{{msg.payload[1]}}_skin.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/eyes/{{msg.payload[2]}}_eyes.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/teeth/{{msg.payload[3]}}_teeth.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/lips/{{msg.payload[4]}}_lips.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/hair/{{msg.payload[5]}}_hair.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/hat/{{msg.payload[6]}}_hat.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/chest/{{msg.payload[7]}}_chest.png" alt="" style="position: absolute; top: 0; left: 0;">
</div>

```

Note: merging the literal files into a single file per NFT, for what was required in the Smart Contract reference, was a slightly different process but followed the same logic.




