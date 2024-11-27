# CyberChallengeX
Fun hacking challenges for everyone!

## _Day 1 Challenge: Initiate Protocol 🌐_

Ready to dive deep into the network void? Let’s boot up the systems and get your brain in gear for Day 1 of CyberChallengeX! 🚀

### 🔎 Scenario:
You’ve just intercepted a suspicious data stream. A packet capture (PCAP) file has surfaced, revealing a strange TCP conversation on port 1337—a beacon from the digital unknown. There’s a message buried within the traffic, encoded and waiting to be uncovered. This is your first mission, and you’ll need all your cyber instincts to crack it.

### 🔑 Your Mission:

Download the PCAP file here: [Phantom Stream pcap](https://github.com/d4n392/CyberChallengeX/blob/main/hacking_challenge_day1.pcapng)

Use Wireshark (or your tool of choice) to sift through the traffic and isolate the hidden message.

Follow the data trail. It’s not encrypted, but it’s definitely encoded—a cipher wrapped in a network packet.

Focus your analysis on the payload—look for patterns, anomalies, and those telltale signs of an encoding scheme in use.

### 💡 Hint:
This isn’t your typical encryption. What you’re dealing with is a classic encoding scheme, a common one. You’ve seen it before, but now it’s disguised in the raw flow of data. Think about how digital data gets encoded when it’s ready to be hidden in plain sight. Decode it and reveal what lies beneath.

Below is a breakdown of finding the answer, try and give it a shot first..._it's much more fun!_

## Day 1 Solution: Unveil the Signal

### 🔎 Scenario Recap

You’re investigating a strange TCP conversation on port 1337—a port known for its iconic hacker culture associations. Within the packet capture, the hidden message is waiting to be decoded. The solution requires your sharp eye and steady hand to decode the Base64-encoded payload nestled in the raw data.

### ⚒️ Tools You'll Use

Wireshark (network protocol analyzer), Basic Python scripting for decoding

### 🛠️ Step-by-Step Instructions

#### Download the PCAP File:

[Phantom Stream pcap](https://github.com/d4n392/CyberChallengeX/blob/main/hacking_challenge_day1.pcapng)

#### Open in Wireshark

#### Load the PCAP into Wireshark.

#### Filter the traffic by port 1337 with this filter:
    tcp.port == 1337

#### Inspect the Packets

Look at the payload in the TCP packets. Navigate to this packet #9, highlight the Data section and in the right-hand "Packet Bytes" pane, you’ll notice the data is encoded. 

"RXhwbG9yZSB0aGUgc3RyZWFtIGZpbmQgdGhlIHRydXRoCg==" _is the payload we are searching for._

![image](https://github.com/user-attachments/assets/d710f3c0-6eb2-4e91-bc1e-85895539f37d)

_Right-click on the payload > Follow TCP Stream to view all the data in one place._

Export the Payload

#### Save the raw data from the TCP stream to a file:

File > Export Packet Bytes... (Ctrl + Shift + X) > Raw Data

Save it as payload.txt.

#### Decode the Data with Python

_The data is Base64-encoded. Here’s a Python script to decode it:_

    python3 -c "import base64; file = open('payload.txt', 'rb'); encoded_data = file.read(); file.close(); decoded_data = base64.b64decode(encoded_data).decode('utf-8'); print('Decoded Message:'); print(decoded_data)"


Run the script, and you’ll see the hidden message revealed.

_Decoded Message:_ 
Explore the stream find the truth 🏴


# 💡 Key Takeaways
Port filtering helps isolate relevant data.
TCP streams allow you to reconstruct full conversations.
Base64 is a common encoding method used in network data—always a good starting point for decoding.

# Conclusion

### Congratulations, I hope you enjoyed your mission Cyberspace Explorer! 🖥️

You've successfully completed Day 1 of CyberChallengeX, where you decoded the mystery of an encrypted TCP stream on port 1337. The hidden message you uncovered—"Explore the stream, find the truth 🏴"—is just the first whisper in a much larger, far-reaching digital landscape.

As you sharpen your skills with every challenge, remember: not everything is as it seems. The network traffic you analyzed? Just the surface layer. Beneath that lies something... far deeper. There are whispers in the packets, fragments in the data—glitches in the matrix.

Day 1 was a warm-up, but the next challenges? They won’t just test your technical know-how—they'll make you question what’s lurking in the digital shadows. Encoding schemes will get more complex. Layers of obfuscation will thicken. And who knows what secrets are hidden in the flow of bits and bytes you're yet to decode?

Stay sharp. The truth is out there—and it’s waiting for you to peel back the layers of the network. 🌐

Get ready for what’s next, because in the world of CyberChallengeX, things are about to get... interesting. 👁️
