---
title: Host a single-page website on IPFS
legacyUrl: https://docs.ipfs.io/guides/examples/websites/
description: Learn how to host a static website on the decentralized web using IPFS.
---

# Host a single-page website on IPFS

In this tutorial, you'll import a simple one-page website to IPFS, have it use the Cloudflare Content Delivery Network (CDN), and link up a domain name so people can find your site easily.

## Install IPFS desktop

IPFS desktop application is the easiest way to get up and running quickly with IPFS. The installation steps for IPFS desktop differ between operating systems. Follow the instructions for your system.

### Windows

1. Go to the [IPFS desktop downloads page](https://github.com/ipfs-shipyard/ipfs-desktop/releases).
2. Find the link ending in `.exe` for the latest version of IPFS desktop:

    ![The IPFS desktop download page.](images/install-windows-download-exe-page.png)

3. Run the `.exe` file to start the installation.
4. Select whether you want to install the application for just yourself, or all users on the computer. Click **Next**:

    ![The IPFS desktop install options window.](images/install-windows-install-options.png)

5. Select the install location for the application. The default location is usually fine. Click **Next**:

    ![The IPFS desktop installation location window.](images/install-windows-install-location.png)

6. Wait for the installation to finish and click **Finish**:

    ![The IPFS desktop installation finished window.](images/install-windows-install-finish.png)

7. You can now find an IPFS icon in the status bar:

    ![The IPFS desktop status bar menu in the Windows status bar.](images/install-windows-ipfs-desktop-status-bar.png)

The IPFS desktop application has finished installing. You can now start to [add your site](#add-your-site).

### MacOS

1. Download the latest available `.dmg` file from the `ipfs-shipyard/ipfs-desktop` GitHub repository:

    ![List of available download links in GitHub.](images/install-macos-dmg-file-link.png)

2. Open the `ipfs-desktop.dmg` file.
3. Drag the IPFS icon into the **Applications** folder:

    ![Drag-to-install window in MacOS.](images/install-macos-drag-ipfs-drag.png)

4. Open your **Applications** folder and open the IPFS desktop application.
5. You may get a warning saying _IPFS Desktop.app can't be opened_. Click **Show in Finder**:

    ![Application cannot be installed error.](images/install-macos-ipfs-cannot-be-opened.png)

6. Find **IPFS Desktop.app** in your **Applications** folder.
7. Hold down the `control` key, click **IPFS Desktop.app**, and click **Open**:

    ![Right click context menu of IPFS Desktop.app.](images/install-macos-force-open.png)

8. Click **Open** in the new window:

    ![Open confirmation window.](images/install-macos-open-confirmation.png)

9. You can now find an IPFS icon in the status bar:

    ![The IPFS desktop status bar menu in the macOS status bar.](images/install-macos-ipfs-desktop-status-bar.png)

The IPFS desktop application has finished installing. You can now start to [add your site](#add-your-site).

### Linux

1. Download the `.deb` package:
1. Open the `.deb` package in **Software Installer**:

    ![Right-click context menu of the IPFS deb package.](images/install-ubuntu-software-install.png)

1. Click **Install** and wait for the installation to finish:

    ![Install screen within the Ubuntu software installation window.](images/install-ubuntu-install.png)

1. Click **Applications** or press the Windows key on your keyboard.
1. Search for `IPFS` and select **IPFS Desktop**:

    ![Ubuntu search screen with IPFS desktop showing.](images/install-ubuntu-search-window.png)

1. You can now find an IPFS icon in the status bar:

    ![IPFS icon shown in the Ubuntu status bar.](images/install-ubuntu-ipfs-running-status-bar.png)

The IPFS desktop application has finished installing. You can now start to [add your site](#add-your-site).

## Add your site

The next step is to import your site into IPFS using the IPFS desktop app you just installed. The website we'll be using is incredibly simple. The purpose of it is to generate a random Hobbit-like name and display it to the visitor. Each time the page is refreshed, a new name is displayed. The website is creatively called _Hobbit name generator_.

1. Create a file called `index.html` and paste in the following code:

    ```html
    <!doctype html>
    <html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Random Planet Facts</title>
        <meta name="description" content="A Get a random fact about a planet in our solar system.">
        <meta name="author" content="The IPFS Docs team.">
        <style>body{margin:15px auto;max-width:650px;line-height:1.2;font-family:sans-serif;font-size:2.0em;color:#fff;background:#444}</style>
    </head>
    <body onload="main()">
        <h1>Random Planet Facts</h1>
        <p id="output_p"></p>
        <script>
            function main() {
                const facts=["Mars is home to the tallest mountain in our solar system.","Only 18 out of 40 missions to Mars have been successful.","Pieces of Mars have fallen to Earth.","One year on Mars is 687 Earth days.","The temperature on Mars ranges from -153 to 20 °C.","One year on Mercury is about 88 Earth days.","The surface temperature of Mercury ranges from -173 to 427°C.","Mercury was first discovered in the 14th century by Assyrian astronomers.","Your weight on Mercury would be 38% of your weight on Earth.","A day on the surface of Mercury lasts 176 Earth days.","The surface temperature of Venus is about 462 °C.","It takes Venus 225 days to orbit the sun.","17th-century Babylonian astronomers first discovered Venus.","Venus is nearly as big as the Earth with a diameter of 12,104 km.","The Earth’s rotation is gradually slowing.","There is only one natural satellite of the planet Earth, the moon.","Earth is the only planet in our solar system not named after a god.","The Earth is the densest planet in the solar system.","A year on Jupiter lasts around 4333 earth days.","The surface temperature of Jupiter is around -108°C.","Babylonian astronomers first discovered Jupiter in the 7th or 8th century.","Jupiter has 4 rings.","A day on Jupiter lasts 9 hours and 55 minutes.","8th century Assyrians first discovered Saturn.","Saturn takes 10756 days to orbit the Sun.","Saturn can be seen with the naked eye.","Saturn is the flattest planet.","Saturn is made mostly of hydrogen.","Four spacecraft have visited Saturn.","William Herschel discovered Uranus in 1781.","A year on Uranus takes 30687 earth days.","Uranus turns on its axis once every 17 hours, 14 minutes.","With a minimum atmospheric temperature of -224°, C Uranus is nearly the coldest planet in the solar system.","Only one spacecraft has flown by Uranus, the Voyager 2.","Neptune was discovered in 1846 by Urbain Le Verrier and Johann Galle.","Neptune has 14 moons.","The average temperature of Neptune is about -201 °C.","There is a 1:20 million scale model of the solar system in Sweden.", "The gap between the Earth and our moon is bigger than the diameters of all the planets combined.", "The first accurate calculation of the speed of light was using Jupiter’s moons", "Jupiter’s magnetic field is believed to be a result of rapidly spinning metallic hydrogen at the core, and is ~10x stronger than the Earth’s.", "Venus spins backward.", "Uranus spins sideways, relative to the ecliptic plane of the solar system.", "It is easier to reach Pluto or escape the solar system from Earth than being able to <i>land</i> on the Sun."];
                document.querySelector('#output_p').innerHTML = facts[Math.floor(Math.random() * facts.length)]
            }
        </script>
    </body>

    </html>
    ```

2. Open IPFS desktop and go to the **Files** page.
3. Click **Add** → **File**.

    ![Add file menu in IPFS desktop.](/images/ipfs-desktop-add-file.png)

4. Navigate to your `index.html` file and select **Open**.

    ![Choose a file window open in IPFS desktop.](/images/ipfs-desktop-open-file.png)

5. Click the triple dot menu on `index.html` and select **Share link**.
6. Click **Copy** to copy the file's URL to your clipboard.

    ![Share files window in IPFS desktop.](/images/ipfs-desktop-share-files.png)

7. Open a browser and paste in the URL you just copied.

Your browser should load the website in a few moments! This can take up to a few minutes the first time. You can move onto the next section while the site is loading.

## Pinning files

IPFS nodes treat the data they store like a cache, meaning that there is no guarantee that the data will continue to be stored. _Pinning_ a file tells an IPFS server that the data is essential and shouldn't be thrown away.

You should _pin_ any content you consider important to ensure that content is retained over the long term. Since data relevant to someone else may not be important to you, pinning enables you to have control over the disk space and data retention you need.

### Using Pinata

To ensure that your important data is retained, you may want to use a pinning service. [Pinata](https://pinata.cloud/) is one such service that offers pinning for free!

1. Go to [Pinata.cloud](https://pinata.cloud/) and sign up or log in.
2. Click [**Pinata Upload**](https://pinata.cloud/pinataupload).
3. Select **Upload File** and click **Browse**.
4. Navigate to your `index.html` file and click **Open**.
5. Click **Upload**.
6. Once the file has finished uploading, click **Pin Explorer** to view any files you have pinned.
7. You should be able to see your `index.html` file pinned:

    ![The Pinata Pin Explorer screen showing the index.html pinnded.](images/pinned-index-file-in-pinata.png)

8. Click the **IPFS Hash** of your `index.html` file to open your website through the Pinata gateway.

    ![Random planet fact website pinned using Pinata and displayed in Firefox](images/pinned-random-planet-fact-website.png)

## Set up a domain

This section is completely optional. 

If you have access to a domain name service like Namecheap, Google Domains, GoDaddy, or any other domain service, then you can follow along with these steps. If you don't have a domain name to assign, then you can just read along through this section. We're going to dive into using services like DNSLink and the Ethereum Naming Service (ENS) in later sections.

We used Namecheap, but the process is very similar across all domain name services.

1. Log into your domain name provider.
2. Go to your domain management window and find the domain you want to assign to your website.
3. Find where to change the **Redirection Settings**.
4. In a new tab, go to the [Pinata Pin Explorer](https://pinata.cloud/pinexplorer) screen.
5. Copy the **IPFS Hash** link.
6. In your domain name providers **Redirection Settings** section, paste in the **IPFS Hash** link you just copied.

    ![Redirecting a source URL to an IPFS Hash link within Namecheap.](images/namecheap-source-url-redirect.png)

7. Save your changes.

Domain name services are fairly slow to update, but in a few hours, you should be able to go to your domain and see the website you pinned using Pinata!

![Random planet facts site with the randomplanetfacts.xyz url](images/random-planets-with-correct-url.png)

## Further improvements

This project was designed to get you up and running quickly, but there are many improvements we can make here.

You may have noticed that when visiting [randomplanetfacts.xyz](https://randomplanetfacts.xyz), your browser redirects to [gateway.pinata.cloud/ipfs/QmW7S5HR...](https://gateway.pinata.cloud/ipfs/QmW7S5HRLkP4XtPNyT1vQSjP3eRdtZaVtF6FAPvUfduMjA).

Another issue is that the website is incredibly simple. There are no images, stylesheets, or javascript files. If you're interested in building a more complex site using IPFS, [carry on with this tutorial series 🡒](#)