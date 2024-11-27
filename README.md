# CyberChallengeX
Fun hacking challenges for everyone!

## _Day 1 Challenge_
Let’s kick things off with a classic puzzle to get your gears turning! 🚀

🔎 Scenario:
You’re analyzing network traffic for a potential breach. A packet capture (PCAP) file reveals an unusual TCP conversation on port 1337. Hidden within the data is a secret message.

🔑 Challenge:

Download the PCAP file here: (https://github.com/d4n392/CyberChallengeX/blob/main/hacking_challenge_day1.pcapng).

Analyze the traffic using Wireshark (or your favorite tool).

Find the hidden message.

💡 Hint: Focus on the payload data. It’s not encrypted, but it’s definitely encoded. Think about common encoding schemes.

Below is the answer, try and give it a shot first 

## _Day 1 Solution_ 
### 🔎 Scenario
You're investigating unusual network activity on port 1337. A packet capture file has been provided, and your goal is to decode the hidden message.

### ⚒️ Tools You'll Use
Wireshark (network protocol analyzer), Basic Python scripting for decoding
### 🛠️ Step-by-Step Instructions
#### Download the PCAP File:
(https://github.com/d4n392/CyberChallengeX/blob/main/hacking_challenge_day1.pcapng)

#### Open in Wireshark

#### Load the PCAP into Wireshark.

#### Filter the traffic by port 1337 with this filter:
tcp.port == 1337

#### Inspect the Packets
Look at the payload in the TCP packets. Navigate to this packet #9, highlight the Data section and in the right-hand "Packet Bytes" pane, you’ll notice the data is encoded. "

![image](https://github.com/user-attachments/assets/d710f3c0-6eb2-4e91-bc1e-85895539f37d)

_Right-click on the payload > Follow TCP Stream to view all the data in one place._

Export the Payload

#### Save the raw data from the TCP stream to a file:
File > Export > Raw Data

Save it as payload.txt.

Decode the Data with Python

_The data is Base64-encoded. Here’s a Python script to decode it:_

import base64

# Read the saved payload
with open('payload.txt', 'rb') as file:
    encoded_data = file.read()

# Decode the data
decoded_data = base64.b64decode(encoded_data).decode('utf-8')

print("Decoded Message:")
print(decoded_data)
Run the script, and you’ll see the hidden message revealed.

Message reveals: 

💡 Key Takeaways
Port filtering helps isolate relevant data.
TCP streams allow you to reconstruct full conversations.
Base64 is a common encoding method used in network data—always a good starting point for decoding.
