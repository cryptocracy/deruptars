# deruptars
avatar element for Deruptars at https://derupt.io

# premise
Creates a "Deruptar" (an avatar), who's properties are based on a given public STX principle deposit address. 

# how
The avatar is the result of a composite of layered png files.

First you'd get STX address in. Then Trim the first 4 Characters. (Trim the SP [or ST if testnet] + next 2 characters.)

Then concat the next 4 digits, with the last 4 digits.

Once you have your 8 digit string, break it into an array and pass that out like such:
```
var depositaddress = "STXADDRESS"; //Your Deposit address

rawaddy = depositaddress.substring(4); //Trim first 4 digits

a1 = rawaddy.substr(0,4); // keep next 4 digits

z1 = rawaddy.substring(rawaddy.length - 4); //keep last 4 digits

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
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/hair/{{msg.payload[4]}}_hair.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/glasses/{{msg.payload[5]}}_glasses.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/hat/{{msg.payload[6]}}_hat.png" alt="" style="position: absolute; top: 0; left: 0;">
<img src="https://raw.githubusercontent.com/cryptocracy/deruptars/main/chest/{{msg.payload[7]}}_chest.png" alt="" style="position: absolute; top: 0; left: 0;">
</div>

```





