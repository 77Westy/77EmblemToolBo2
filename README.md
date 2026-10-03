# 77 BO2 Emblem Toolkit

**Made by 77 West**

Create Black Ops II emblems from images, capture existing emblems, and load a selected emblem into your own in-game editor. Includes a local image converter, a searchable library of 261 mapped shape IDs, emblem previews, and a black-and-red 77 interface.

[Join the 77 Discord](https://discord.gg/9qDSeNJMBc)

## What you need

- A Windows PC for the packaged EXE.
- A PlayStation with access to the BO2 online emblem editor. The original toolkit documents PS5 setup; other console/game configurations are not independently verified by this project.
- The PC and PlayStation connected to the same local network/router.
- An internet connection and your usual PlayStation Network sign-in for online game features.
- The toolkit running on the PC while the console uses its proxy.

**You configure the proxy on your PlayStation's network connection—not on your PSN account. You do not enter your PSN password into this tool.**

## 1. Start the toolkit

### Windows app

1. Download the 77 Windows EXE from this repository's **Releases** section, if a release has been published.
2. Put it in its own writable folder, such as `Documents\77 Emblem Toolkit`.
3. Run `77EmblemToolkit.exe` or `77EmblemStudio.exe`, depending on the release filename.
4. Keep the app's terminal window open.
5. The interface should open in your browser. If it does not, visit **http://localhost:8090** on the PC.

Python is not required for the packaged EXE. The app creates its `saved` folder beside the EXE when emblems are imported or captured.

### Run from source

Install Python 3.10 or newer, extract the complete project, then run **START_77.bat** on Windows. The launcher installs the required dependency and starts the app.

Alternatively, run these commands from the project folder:

```bash
python -m pip install -r requirements.txt
python run.py
```

## 2. Connect your PlayStation to the PC proxy

Start the toolkit **before** configuring the console. Look for the proxy address in the toolkit header or terminal.

Example only:

| Setting | Example |
| --- | --- |
| Proxy address | `192.168.1.42` |
| Proxy port | `8080` |
| PC control panel | `http://localhost:8090` |

**Use your own PC's displayed address. Do not copy the example IP. Do not enter `localhost`, `127.0.0.1`, or port `8090` on the PlayStation.**

### PS5

1. Open **Settings → Network → Settings → Set Up Internet Connection**.
2. Select your connected Wi-Fi or wired LAN connection and open **Advanced Settings**. The Options button may expose this menu.
3. Change **Proxy Server** to **Use**.
4. Enter the PC's displayed local IP address and proxy port **8080**.
5. Keep your existing IP, DNS and MTU settings unless your network requires something different.
6. Save/apply the settings and test the internet connection.
7. Sign in to PSN normally, then start BO2 and access Multiplayer.

If Windows Firewall asks about the app, allow it on your trusted **Private** network so your console can reach the PC. Do not disable your firewall or antivirus.

### PS4 network settings

The PS4 proxy menu is under **Settings → Network → Set Up Internet Connection → Use Wi-Fi / Use a LAN Cable → Custom**. Keep the appropriate existing settings, then choose **Proxy Server → Use** and enter the PC IP and port `8080`.

These are network configuration steps, not a claim that every PS4 BO2 setup is supported. Your game configuration must expose the compatible online emblem requests.

## 3. Create an emblem from an image

1. In the toolkit, click **Create emblem from an image**.
2. Upload, drag in, or paste your image.
3. Choose the converter's quality/settings and start conversion.
4. Wait for results, then select the version you prefer.
5. Enter a name and click **Add to 77 collection**.
6. Return to the toolkit. Your new emblem appears in **Your collection**.

The converter runs locally in your browser using bundled scripts and shape images. You do not need to open the external converter website. It approximates the image with up to **32 BO2 layers**; it does not upload the original PNG directly into the game.

## 4. Import an existing Load Code

1. Paste the **complete Load Code** into **Import custom emblem**.
2. Enter an emblem name.
3. Click **Import emblem**.
4. Check the preview in your collection.

The importer supports the compressed Load Code format used by the bundled reference editor. A PNG, screenshot, or build-sheet table is not a Load Code.

## 5. Capture an existing emblem

1. Set the toolkit to **Capture**.
2. In BO2, open the player's profile/channel that requests the emblem.
3. Wait for the emblem to appear in your collection.
4. Rename it if desired.

Capture depends on the console requesting the emblem through the proxy. A cached emblem might not generate a new request immediately.

## 6. Show the emblem and save it in-game

1. Click an emblem in **Your collection** to select it.
2. Choose **Show**.
3. **Restart BO2, or switch to Zombies and back to Multiplayer, before opening your emblem editor.** The game can cache emblem data during a session.
4. Open your own **Emblem Editor** and enter editing for your custom emblem.
5. Check the actual in-game preview and layers.
6. Save it using the game's save option.

A selected card in the toolkit is not proof that the console received the emblem. A blank thumbnail on the game's selection screen is also not the same as checking the emblem inside the editor. Confirm the editor preview before saving.

**Locked shapes:** your account must have the required shapes/icons unlocked. The toolkit does not bypass the game's unlock requirements.

## Modes

| Mode | What it does |
| --- | --- |
| Off | Passes traffic through without capturing or substituting emblems. |
| Capture | Saves emblem responses requested by the console. |
| Show | Answers compatible emblem requests with your selected emblem. |

**Off does not remove the console's proxy setting.** If the console still points to the PC, keep the toolkit running or disable the proxy on the console.

## When you finish

1. Return to the PlayStation network settings.
2. Set **Proxy Server → Do Not Use**.
3. Apply the settings.
4. Close the toolkit.

Leaving the proxy enabled while the PC/app is off can prevent the console from reaching services that use that proxy.

## Troubleshooting

### PlayStation cannot connect after enabling the proxy

- Keep the toolkit running and the PC awake.
- Check that both devices are on the same local network, not an isolated guest Wi-Fi network.
- Verify the PC IP and port `8080`; the local IP can change after reconnecting or restarting.
- Check Windows Firewall access for the app on the trusted private network.
- Temporarily set the console proxy to **Do Not Use** to restore its normal connection while troubleshooting.

### The emblem appears in the toolkit but is blank in-game

- Select the correct card and confirm **Show** mode.
- Restart BO2 or switch Zombies → Multiplayer before opening the editor.
- Verify that the console uses the running PC's proxy.
- Check the emblem inside the editor, not only on the selection screen.
- Try a known captured emblem to help distinguish proxy issues from conversion issues.
- Enable **Debug log**, reproduce the issue, then use **Open logs folder**.

### Import reports an unsupported shape

Copy the complete error message. If a mapping needs correction, save and capture a separate in-game emblem containing **only that shape**. Provide its `slot_*.bin` and the shape name when requesting support. Do not guess IDs from a website's list order.

### Old design still appears

Close any older running toolkit, start the new version and press **Ctrl+F5** in the browser.

### Keep your emblems when updating

Close the app and back up its **saved** folder. Copy that folder beside the new EXE or into the new extracted project folder. Do not overwrite your only backup.

## Coverage and limits

- 261 mapped shape IDs: tools, letters/numbers, ranks, gear and emblems.
- Up to 32 layers per emblem.
- Supports layer order, color, opacity, rotation, position, scale and mirroring from the reference-editor Load Code.
- Full catalog coverage does not mean every inherited mapping has been independently verified on every console.
- Local previews and automated conversion checks do not replace live game testing.

## Support

[Join the 77 Discord](https://discord.gg/9qDSeNJMBc). Include the app version, console/game setup, exact error, and relevant debug log. Never post your PSN password or other account credentials.

## Credits

**77 branding and custom integration: Made by 77 West.**

Built on these project:

- [BO2 Emblem Toolkit — alexkotr1](https://github.com/alexkotr1/bo2-emblem-toolkit)

Original license notices and third-party attribution are retained with the project. This is an independent community tool, not an official Activision, Treyarch, Sony or PlayStation product.

Network setup reference: [PlayStation internet connection support](https://www.playstation.com/en-us/support/connectivity/internet-connect-playstation/).
