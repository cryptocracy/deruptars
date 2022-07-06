# deruptars
Indivial avatar element for Deruptars NFTs, part of the Derupt Alpha Experience at https://mia.derupt.io 

# premise
Creates a "Deruptar" (an avatar), who's properties are based on a given public STX principal deposit address. 

# how
The avatar is the result of a composite of layered png files.

First you'd get STX address in. Then Trim the first 4 Characters. (Trim the SP [or ST if testnet] + next 2 characters.)

Then concat the next 4 digits, with the last 4 digits.

```
var depositaddress = "STXADDRESS"; //Your Deposit address

var rawaddy = depositaddress.substring(4); //Trim first 4 digits

var a1 = rawaddy.substr(0,4); // keep next 4 digits

var z1 = rawaddy.substring(rawaddy.length - 4); //keep last 4 digits

msg.payload = a1+z1; // concat both and pass string along

return msg;
```
Then you'd want to split string into an array looking like this.
```
{
   "payload":["A","8","4","J","A","R","7","M"]
}
```
Then you'd passed into a composite template looking something like....
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





