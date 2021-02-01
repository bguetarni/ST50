Project repository: [ bguetarni /
Egocentric-activity-recognition ](https://github.com/bguetarni/Egocentric-activity-recognition)

# utbm-latex-internship-report-covers

A LaTeX version of the UTBM internship report covers using TikZ.

You can compare [the original version](original-version.doc) and [the LaTeX version](latex-version.pdf).

# Warning
This is a forked repo from [utbm-latex-internship-report-covers](https://github.com/pinam45/utbm-latex-internship-report-covers).


**UTBM and all UTBM-related trademarks and logos are trademarks or registered trademarks of University of Technology of Belfort-Montbéliard in France, other countries, or both.**

# Requirements

The package require the Tahoma font as the original covers use it.

To load the Tahoma font, the fontspec package is used which means the document must be compiled with *xelatex* or *lualatex* (at the moment not lualatex because of a [pgf bug](https://sourceforge.net/p/pgf/bugs/384/)).

### Install LaTex
```
sudo apt install texlive-latex-extra
sudo apt-get install texlive-fonts-extra
sudo apt-get install texlive-lang-french
sudo apt-get install texlive-xetex
```

### Install Tahoma
```
wget https://sourceforge.net/projects/corefonts/files/OldFiles/IELPKTH.CAB
apt install cabextract
cabextract -F 'tahoma*ttf' IELPKTH.CAB
mkdir -p /usr/share/fonts/truetype/msttcorefonts/
mv -f tahoma*ttf /usr/share/fonts/truetype/msttcorefonts/
chmod 644 /usr/share/fonts/truetype/msttcorefonts/tahoma*
fc-cache -v
rm -f IELPKTH.CAB
```
(https://askubuntu.com/questions/438670/install-tahoma-font-in-ubuntu)

### Install LaTEX extension for VSCode
https://github.com/James-Yu/LaTeX-Workshop

# Installation

## Install the package

Copy the directory [utbmcovers](utbmcovers) inside one of your **texmf** directory: to follow the TDS (TeX Directory Structure), copy it in ``<texmf_folder>/tex/latex/``.

Your **texmf** directory is usually ``$HOME/texmf`` on Unix operating systems.

On Windows with MiKTeX you can find it in MiKTeX's options:
- Start menu -> MiKTeX -> MiKTeX settings
- The options window should open
- Go in the *Roots* panel
- Check *Show MiKTeX-maintained root directories*
- Take the path with the description: "CommonData, CommonConfig" (It is usually ``C:\ProgramData\MiKTeX\<version>``) or add the path you want

## Refresh the LaTeX databases

On Unix operating systems, in root:
```
$> mktexlsr
$> update-updmap --quiet
```

On Windows with MiKTeX
- Start menu -> MiKTeX -> MiKTeX settings
- Click *Refresh FNDB*
- Click *Update Formats*

# Usage

Include the package:
```latex
\usepackage{utbmcovers}
```
Configure the displayed information:
```
\setutbmfrontillustration{Illustration_file}
\setutbmtitle{Title}
\setutbmsubtitle{Subtitle}
...
```
Use ``\makeutbmfrontcover{}`` to print the front cover and ``\makeutbmbackcover{}`` to print the back cover.

See [latex-version.tex](latex-version.tex) for a complete example.

# Usage with upmethodology

The **tex-upmethodology** collection of packages available on [arakhne.org](http://www.arakhne.org/tex-upmethodology) and on [CTAN](https://www.ctan.org/pkg/upmethodology).

An upmethodology extension is included with the package, in your ``.tex`` document using the document class **upmethodology-document** put:
```latex
\UseExtension{utbmcovers}
```
before using the *utbmcovers* configuration functions.

See [latex-upmethodology-version.tex](latex-upmethodology-version.tex) for a complete example.

# Other
To include a glossary, compile by hand with: ```makeglossaries filename```

To include a bibliography managed by an external file, compile by hand with: ```bibtex filename.aux```
