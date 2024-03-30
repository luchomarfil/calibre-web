# Short Notice from the maintainer 

After 6 years of more or less intensive programming on Calibre-Web, I need a break. 
The last few months, maintaining Calibre-Web has felt more like work than a hobby. I felt pressured and teased by people to solve "their" problems and merge PRs for "their" Calibre-Web. 
I have turned off all notifications from Github/Discord and will now concentrate undisturbed on the development of “my” Calibre-Web over the next few weeks/months.  
I will look into the issues and maybe also the PRs from time to time, but don't expect a quick response from me.

# Calibre-Web

Calibre-Web is a web app that offers a clean and intuitive interface for browsing, reading, and downloading eBooks using a valid [Calibre](https://calibre-ebook.com) database.

[![License](https://img.shields.io/github/license/janeczku/calibre-web?style=flat-square)](https://github.com/janeczku/calibre-web/blob/master/LICENSE)
![Commit Activity](https://img.shields.io/github/commit-activity/w/janeczku/calibre-web?logo=github&style=flat-square&label=commits)
[![All Releases](https://img.shields.io/github/downloads/janeczku/calibre-web/total?logo=github&style=flat-square)](https://github.com/janeczku/calibre-web/releases)
[![PyPI](https://img.shields.io/pypi/v/calibreweb?logo=pypi&logoColor=fff&style=flat-square)](https://pypi.org/project/calibreweb/)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/calibreweb?logo=pypi&logoColor=fff&style=flat-square)](https://pypi.org/project/calibreweb/)
[![Discord](https://img.shields.io/discord/838810113564344381?label=Discord&logo=discord&style=flat-square)](https://discord.gg/h2VsJ2NEfB)

<details>
<summary><strong>Table of Contents</strong> (click to expand)</summary>

1. [About](#calibre-web)
2. [Features](#features)
3. [Installation](#installation)
   - [Installation via pip (recommended)](#installation-via-pip-recommended)
   - [Quick start](#quick-start)
   - [Requirements](#requirements)
4. [Docker Images](#docker-images)
5. [Contributor Recognition](#contributor-recognition)
6. [Contact](#contact)
7. [Contributing to Calibre-Web](#contributing-to-calibre-web)

</details>


*This software is a fork of [library](https://github.com/mutschler/calibreserver) and licensed under the GPL v3 License.*

![Main screen](https://github.com/janeczku/calibre-web/wiki/images/main_screen.png)

## Features

- Modern and responsive Bootstrap 3 HTML5 interface
- Full graphical setup
- Comprehensive user management with fine-grained per-user permissions
- Admin interface
- Multilingual user interface supporting 20+ languages ([supported languages](https://github.com/janeczku/calibre-web/wiki/Translation-Status))
- OPDS feed for eBook reader apps
- Advanced search and filtering options
- Custom book collection (shelves) creation
- eBook metadata editing and deletion support
- Metadata download from various sources (extensible via plugins)
- eBook conversion through Calibre binaries
- eBook download restriction to logged-in users
- Public user registration support
- Send eBooks to E-Readers with a single click
- Sync Kobo devices with your Calibre library
- In-browser eBook reading support for multiple formats
- Upload new books in various formats, including audio formats
- Calibre Custom Columns support
- Content hiding based on categories and Custom Column content per user
- Self-update capability
- "Magic Link" login for easy access on eReaders
- LDAP, Google/GitHub OAuth, and proxy authentication support

## Installation

#### Installation via pip (recommended)
1. Create a virtual environment for Calibre-Web to avoid conflicts with existing Python dependencies
2. Install Calibre-Web via pip: `pip install calibreweb` (or `pip3` depending on your OS/distro)
3. Install optional features via pip as needed, see [this page](https://github.com/janeczku/calibre-web/wiki/Dependencies-in-Calibre-Web-Linux-and-Windows) for details
4. Start Calibre-Web by typing `cps`

*Note: Raspberry Pi OS users may encounter issues during installation. If so, please update pip (`./venv/bin/python3 -m pip install --upgrade pip`) and/or install cargo (`sudo apt install cargo`) before retrying the installation.*

Refer to the Wiki for additional installation examples: [manual installation](https://github.com/janeczku/calibre-web/wiki/Manual-installation), [Linux Mint](https://github.com/janeczku/calibre-web/wiki/How-To:-Install-Calibre-Web-in-Linux-Mint-19-or-20), [Cloud Provider](https://github.com/janeczku/calibre-web/wiki/How-To:-Install-Calibre-Web-on-a-Cloud-Provider).

## Quick Start

1. Open your browser and navigate to `http://localhost:8083` or `http://localhost:8083/opds` for the OPDS catalog
2. Log in with the default admin credentials
3. If you don't have a Calibre database, you can use [this database](https://github.com/janeczku/calibre-web/raw/master/library/metadata.db) (move it out of the Calibre-Web folder to prevent overwriting during updates)
4. Set `Location of Calibre database` to the path of the folder containing your Calibre library (metadata.db) and click "Save"
5. Optionally, use Google Drive to host your Calibre library by following the [Google Drive integration guide](https://github.com/janeczku/calibre-web/wiki/G-Drive-Setup#using-google-drive-integration)
6. Configure your Calibre-Web instance via the admin page, referring to the [Basic Configuration](https://github.com/janeczku/calibre-web/wiki/Configuration#basic-configuration) and [UI Configuration](https://github.com/janeczku/calibre-web/wiki/Configuration#ui-configuration) guides

#### Default Admin Login:
- **Username:** admin
- **Password:** admin123

## Requirements

- Python 3.5+
- [Imagemagick](https://imagemagick.org/script/download.php) for cover extraction from EPUBs (Windows users may need to install [Ghostscript](https://ghostscript.com/releases/gsdnld.html) for PDF cover extraction)
- Optional: [Calibre desktop program](https://calibre-ebook.com/download) for on-the-fly conversion and metadata editing (set "calibre's converter tool" path on the setup page)
- Optional: [Kepubify tool](https://github.com/pgaskin/kepubify/releases/latest) for Kobo device support (place the binary in `/opt/kepubify` on Linux or `C:\Program Files\kepubify` on Windows)

## Docker Images

Pre-built Docker images are available in the following Docker Hub repositories (maintained by the LinuxServer team):

#### **LinuxServer - x64, aarch64**
- [Docker Hub](https://hub.docker.com/r/linuxserver/calibre-web)
- [GitHub](https://github.com/linuxserver/docker-calibre-web)
- [GitHub - Optional Calibre layer](https://github.com/linuxserver/docker-mods/tree/universal-calibre)

  Include the environment variable `DOCKER_MODS=linuxserver/mods:universal-calibre` in your Docker run/compose file to add the Calibre `ebook-convert` binary (x64 only). Omit this variable for a lightweight image.

  Both the Calibre-Web and Calibre-Mod images are automatically rebuilt on new releases and updates.

  - Set "path to convertertool" to `/usr/bin/ebook-convert`
  - Set "path to unrar" to `/usr/bin/unrar`

## Contributor Recognition

We would like to thank all the [contributors](https://github.com/janeczku/calibre-web/graphs/contributors) and maintainers of Calibre-Web for their valuable input and dedication to the project. Your contributions are greatly appreciated.

## Contact

Join us on [Discord](https://discord.gg/h2VsJ2NEfB)

For more information, How To's, and FAQs, please visit the [Wiki](https://github.com/janeczku/calibre-web/wiki)

## Contributing to Calibre-Web

Check out our [Contributing Guidelines](https://github.com/janeczku/calibre-web/blob/master/CONTRIBUTING.md)


#Para elaborar todo el circuito se requiere de este repo y del repo de docker-calibre-web
* Pasos en este remo /luchomarfil/calibre-web
*) Commit y push de calibre web
*) Crear la release de calibre-web en Github y 
*) Regenerar el tag de docker-calibre-web que es el que chupa calibre-web
git tag -a "20240401" -m "20240401"
git push origin "20240401"
* Pasos con el repo docker-calibre-web. 
* parados en ese repo y con el tag creado, entonces
*) Docker build de la version
luchomarfil/soft:docker-calibre-web-20240401
*) probamos la imagen
*)Docker push de docker-calibre-web


Aquí está el texto ordenado de manera más clara y presentable:

---

## Configuración del circuito entre "calibre-web" y "docker-calibre-web"

Para establecer el circuito completo, se necesita trabajar tanto en el repositorio "calibre-web" como en el repositorio "docker-calibre-web".

### Pasos en el repositorio "/luchomarfil/calibre-web":

1. **Commit y Push de Calibre-Web**:
   - Realiza los cambios necesarios en el código de Calibre-Web.
   - Ejecuta los siguientes comandos:
     ```bash
     git add .
     git commit -m "Descripción del commit"
     git push origin tu_rama
     ```

2. **Crear la Release de Calibre-Web en GitHub**:
   - Crea una nueva release en GitHub con la versión correspondiente.

3. **Regenerar el Tag en docker-calibre-web**:
   - En el repositorio "docker-calibre-web":
     ```bash
     git tag -a "20240401" -m "20240401"
     git push origin "20240401"
     ```

### Pasos en el repositorio "docker-calibre-web":
0. **Mergear el fork externo con la nueva version si se desea**

1. **Docker Build de la versión**:
   - Con el tag creado, dirígete al repositorio "docker-calibre-web" y ejecuta:
     ```bash
     docker build -t luchomarfil/soft:docker-calibre-web-20240401 .
     ```

2. **Probar la Imagen**:
   - Antes de continuar, asegúrate de probar la imagen localmente para verificar su funcionamiento.

3. **Docker Push de docker-calibre-web**:
   - Finalmente, realiza el push de la imagen Docker al registro correspondiente:
     ```bash
     docker push luchomarfil/soft:docker-calibre-web-20240401
     ```

---

Este formato estructurado y claro presenta los pasos necesarios para configurar el circuito entre "calibre-web" y "docker-calibre-web" de manera más legible y comprensible.
