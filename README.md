# CS-12: Wi-Fi Security Assessment

**3MTT NextGen Cohort — Cybersecurity Track**

A simple, step-by-step guide to completing this project using only your Android phone — no computer needed.

*Wani sauƙaƙan jagora, mataki-mataki, don kammala wannan project da wayarka kawai — babu bukatar kwamfuta.*

---

## What is this project? / Menene wannan project?

**EN:** We are checking how secure a Wi-Fi network is — using our own phone as the network, so nothing unsafe or unauthorized is touched. Think of it like checking whether a door has a good lock. We'll look at the "lock" (password/security type) and the "doors" (ports) of our own test network.

**HA:** Za mu duba yadda Wi-Fi network yake da tsaro — ta amfani da wayarmu a matsayin network din, don kada mu taɓa wani abu da ba namu ba. Ka yi tunanin kamar duba ko kofa tana da kyakkyawan kulle. Za mu duba "kullen" (password/security) da "kofofin" (ports) na network dinmu na gwaji.

> ⚠️ **Important / Muhimmi:** We only ever test our OWN hotspot. Never scan or test anyone else's Wi-Fi. / Kullum za mu gwada hotspot dinmu KAWAI. Kada a taɓa gwada Wi-Fi na wani mutum.

---

## What you need / Abin da kake bukata

- Your phone / Wayarka
- A second phone to borrow (a friend's or family member's, just for a few minutes) / Waya ta biyu (ta aboki ko dan'uwa, na 'yan mintuna kadan)

That's it — no computer, no special equipment. / Wannan ke nan — babu bukatar kwamfuta ko wani kayan aiki na musamman.

---

## Step 1: Create your test network / Kafa network din gwajinka

**EN:** Turn your phone into a mobile hotspot. This becomes the network we'll test.

1. Open **Settings**
2. Go to **Network & Internet** (may be called "Hotspot & Tethering" on your phone)
3. Turn on **Mobile Hotspot**
4. Give it a name, for example: `CS12-Test`
5. Set a password (any password for now)

**HA:** Mayar da wayarka zuwa mobile hotspot. Wannan zai zama network din da za mu gwada.

1. Bude **Settings**
2. Je zuwa **Network & Internet** (ana iya kiran shi "Hotspot & Tethering" a wayarka)
3. Kunna **Mobile Hotspot**
4. Sa masa suna, misali: `CS12-Test`
5. Sa password (kowanne password a yanzu)

![Hotspot Settings](screenshots/01_hotspot_settings.jpg)

---

## Step 2: Connect the second phone / Hada waya ta biyu

**EN:** Borrow a second phone and connect it to your hotspot (search for your hotspot's name in their WiFi settings, enter the password).

**HA:** Ka aro waya ta biyu ka hada ta zuwa hotspot dinka (a WiFi settings dinta, ka nemo sunan hotspot dinka, ka shigar da password).

![Second Device Connected](screenshots/02_connected_device.jpg)

---

## Step 3: Install Termux / Shigar da Termux

**EN:** Termux is a free app that lets you type simple commands on your phone, similar to a computer. We'll use it to run one small tool called Nmap.

1. Open **Play Store** or **F-Droid**
2. Search for **Termux**
3. Install it
4. Open it — you'll see a black screen with text, that's normal

**HA:** Termux wata app ce kyauta da ke baka damar rubuta sauƙaƙan commands a wayarka, kamar kwamfuta. Za mu yi amfani da ita don gudanar da wata karamar tool mai suna Nmap.

1. Bude **Play Store** ko **F-Droid**
2. Nemo **Termux**
3. Shigar da ita
4. Bude ta — za ka ga baƙar fuska da rubutu, wannan al'ada ce

![Termux Download](screenshots/03_termux_download.jpg)
![Termux First Launch](screenshots/04_termux_first_launch.jpg)

---

## Step 4: Set up Nmap / Shirya Nmap

**EN:** Inside Termux, type each line below, then press Enter. Wait for each one to finish before typing the next.

**HA:** A cikin Termux, rubuta kowanne layi da ke kasa, sannan ka danna Enter. Ka jira kowanne ya gama kafin ka rubuta na gaba.

```bash
pkg update
```
*(if it asks a question, type `Y` and press Enter / in ya yi tambaya, rubuta `Y` sannan ka danna Enter)*

```bash
pkg install nmap
```
*(same — type `Y` if asked / haka nan — rubuta `Y` in an tambaya)*

![pkg update Result](screenshots/05_pkg_update.jpg)
![Nmap Install Result](screenshots/06_nmap_install.jpg)

---

## Step 5: Find your network address / Nemo adireshin network dinka

**EN:** On the second phone (the one you connected), go to WiFi settings, tap on the connected network, and find the **"IP address"**. It will look like `192.168.x.x`. Write down the first three numbers — for example if it shows `192.168.43.25`, your network address is `192.168.43.0/24`.

**HA:** A waya ta biyu (wanda ka hada), je zuwa WiFi settings, danna network din da aka hada, sannan ka nemo **"IP address"**. Zai yi kama da `192.168.x.x`. Ka rubuta lambobi uku na farko — misali in ya nuna `192.168.43.25`, adireshin network dinka shine `192.168.43.0/24`.

![IP Address in WiFi Settings](screenshots/07_ip_address.jpg)

---

## Step 6: Find connected devices / Nemo na'urorin da suka hade

**EN:** Back in Termux, type this (replace the number with what you found in Step 5):

```bash
nmap -sn 192.168.43.0/24
```

This shows every device connected to your network.

**HA:** A Termux, rubuta wannan (ka canza lambar da wanda ka samu a Mataki na 5):

```bash
nmap -sn 192.168.43.0/24
```

Wannan zai nuna maka duk na'urorin da suka hade da network dinka.

![Device Scan Result](screenshots/08_device_scan.jpg)

---

## Step 7: Check for open ports / Duba open ports

**EN:** Ports are like doors on a device. Some doors are supposed to be open (for normal apps to work); too many open doors can be risky. Pick one of the addresses you found in Step 6, and type:

```bash
nmap 192.168.43.25
```
*(use the actual address you found, not this example)*

This shows which "doors" are open on that device.

**HA:** Ports kamar kofofi ne a na'ura. Wasu kofofin dole su kasance a bude (don apps su yi aiki); kofofi da yawa a bude na iya zama hadari. Zabi daya daga cikin adireshin da ka samu a Mataki na 6, ka rubuta:

```bash
nmap 192.168.43.25
```
*(yi amfani da ainihin adireshin da ka samu, ba wannan misali ba)*

Wannan zai nuna maka wadanne "kofofi" ne a bude a wannan na'ura.

![Port Scan Result](screenshots/09_port_scan.jpg)

---

## Step 8: Check the Wi-Fi's security type / Duba irin security na Wi-Fi

**EN:** On the second phone (the one connected as a client — this step won't work properly on the hotspot phone itself), go to WiFi settings and tap on the connected network. Look for:

- **Security** — should say something like WPA2 or WPA3
- **Signal strength**

Write these down or screenshot them.

**HA:** A waya ta biyu (wadda aka hada a matsayin client — wannan mataki ba zai yi aiki sosai a wayar hotspot dinka kanta ba), je zuwa WiFi settings, danna network din da aka hade. Nemo:

- **Security** — ya kamata ya nuna kamar WPA2 ko WPA3
- **Signal strength**

Ka rubuta ko ka dauki screenshot.

![Security Type in WiFi Settings](screenshots/10_security_type.jpg)

---

## Step 9: Compare a weak and strong password / Kwatanta password mai sauƙi da mai karfi

**EN:** Go back to your hotspot settings.

1. First, set the password to something weak, like `12345678`. Notice that your phone allows it without warning you.
2. Then change it to something strong, like `CS12@Secure2026!` (letters, numbers, and symbols).

**HA:** Koma zuwa hotspot settings dinka.

1. Da farko, sa password mai sauƙi, kamar `12345678`. Ka lura cewa wayarka za ta karɓe shi ba tare da gargaɗi ba.
2. Sannan ka canza zuwa mai karfi, kamar `CS12@Secure2026!` (haruffa, lambobi, da alamomi).

![Weak Password Set](screenshots/11_weak_password.jpg)
![Strong Password Set](screenshots/12_strong_password.jpg)

---

## Step 10: Write your findings / Rubuta abin da ka gano

**EN:** Fill in this table with what you actually found:

**HA:** Cika wannan table da abin da ka samu ainihi:

| Question / Tambaya | Your Answer / Amsarka |
|---|---|
| How many devices were on the network? / Nawa na'urori ne a network din? | |
| What security type did it use (WPA2/WPA3)? / Wane irin security ne (WPA2/WPA3)? | |
| What ports were open? / Wadanne ports ne a bude? | |
| Did the weak password get accepted? / Shin an karɓi password mai sauƙi? | |

![Completed Findings Table](screenshots/13_findings_table.jpg)

---

## Step 11: What does it all mean? / Menene ma'anarsa?

**EN:**
- If your network uses **WPA2 or WPA3** — that's good, but WPA3 is stronger if your phone supports it.
- An **open port** isn't automatically dangerous — but any port that isn't needed should be closed.
- If a **weak password was accepted without warning** — that's a real weakness. Phones don't stop you from choosing a bad password; you have to choose a strong one yourself.

**HA:**
- In network dinka yana amfani da **WPA2 ko WPA3** — wannan yana da kyau, amma WPA3 ya fi karfi in wayarka ta goyi baya.
- **Open port** ba lallai ne hadari ba — amma duk wani port da ba a bukata ya kamata a rufe.
- In an **karɓi password mai sauƙi ba tare da gargaɗi ba** — wannan raunin tsaro ne na gaskiya. Wayoyi ba sa hana ka zabar mummunan password; dole ne ka zabi mai karfi da kanka.

---

## Step 12: Recommendations / Shawarwari

**EN:**
1. Use WPA3 if your device supports it.
2. Always choose a strong password yourself (12+ characters, mixed letters/numbers/symbols).
3. Turn off your hotspot when you're not using it.
4. Check occasionally for devices connected that you don't recognize.

**HA:**
1. Yi amfani da WPA3 in na'urarka ta goyi baya.
2. Kullum zabi password mai karfi da kanka (haruffa 12+, cakuda haruffa/lambobi/alamomi).
3. Kashe hotspot dinka idan ba kana amfani da shi ba.
4. Ka rika duba idan akwai baƙon na'ura da ta hade da network dinka.

---

## Step 13: Record your demo video / Yi rikodin demo video dinka

**EN:** Record a 2–3 minute video of yourself explaining, in your own words:
1. What this project is about
2. What you did (show the steps briefly)
3. What you found
4. Your recommendation

**Important:** This must be YOUR OWN explanation, in your own words — this is how they confirm the work is really yours.

**HA:** Yi rikodin bidiyo na minti 2-3 na kanka, kana bayani, da kalmominka:
1. Menene wannan project game da shi
2. Abin da ka yi (nuna matakan a takaice)
3. Abin da ka gano
4. Shawararka

**Muhimmi:** Dole ne wannan ya zama BAYANINKA na kanka, da kalmominka — haka ake tabbatar da cewa aikin naka ne da gaske.

---

## Screenshot Checklist / Jerin Screenshots

Put all your screenshots in a folder called `screenshots/`:

| # | What to screenshot |
|---|---|
| 01 | Hotspot settings screen |
| 02 | Second phone connected |
| 03 | Termux download page |
| 04 | Termux first open |
| 05 | `pkg update` result |
| 06 | `nmap` install result |
| 07 | IP address shown in WiFi settings |
| 08 | Device scan result |
| 09 | Port scan result |
| 10 | Security type shown in WiFi settings |
| 11 | Weak password set |
| 12 | Strong password set |
| 13 | Your completed findings table |

---

## A note on doing this honestly / Bayani kan yin wannan da gaskiya

**EN:** Everyone in the CS-12 group is welcome to discuss ideas and help each other understand the steps. But each person must run their own tests, take their own screenshots, and record their own video. Copying someone else's work won't be accepted, and it also means you won't actually learn the skill.

**HA:** Kowa a cikin kungiyar CS-12 yana da 'yanci ya tattauna ra'ayoyi kuma ya taimaki wani ya fahimci matakan. Amma kowanne mutum dole ne ya yi nasa gwajin, ya dauki nasa screenshots, kuma ya yi nasa video. Kwafin aikin wani ba za a karba ba, kuma hakan yana nufin ba za ka koyi kwarewar ba da gaske.

---

*Questions? Ask in the group — someone will help. / Tambayoyi? Ka tambaya a group, wani zai taimaka.*
