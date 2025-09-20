How to show chinese fonts on xpdf

Method1
🔹 1. Install Chinese Fonts

Windows usually comes with SimSun (宋体), SimHei (黑体), Microsoft YaHei (微软雅黑), etc.

If you don’t see them, you can install open-source Chinese fonts like WenQuanYi Zen Hei or Noto Sans CJK from Google.

🔹 2. Locate or Create the Xpdf Config File

In Windows, Xpdf looks for xpdfrc.

By default, it can be in the same folder as xpdf.exe or in your user folder (C:\Users\<YourName>\xpdfrc).

If it doesn’t exist, just create a new text file named xpdfrc.

🔹 3. Add Font Mappings in xpdfrc

Open xpdfrc in Notepad and add something like this (adjust paths to match your system):

# Simplified Chinese font mapping
displayFontTT   Adobe-GB1   C:\Windows\Fonts\simsun.ttc
displayFontTT   Adobe-GB1   C:\Windows\Fonts\simhei.ttf
displayFontTT   Adobe-GB1   C:\Windows\Fonts\msyh.ttc


This tells Xpdf to use your Windows fonts when rendering Chinese text.

🔹 4. Restart Xpdf

Close and reopen Xpdf.

Open a PDF with Chinese text — it should now render properly.

🔹 5. Alternative (if still broken)

Install poppler-data package (it contains CMap and Unicode mapping files for CJK).

You can download from: https://poppler.freedesktop.org

Put the poppler-data files in the same directory as Xpdf or reference them in xpdfrc with:

cidToUnicode   Adobe-GB1   C:\path\to\poppler-data\cidToUnicode\Adobe-GB1.cidToUnicode
cMapDir        Adobe-GB1   C:\path\to\poppler-data\CMap\Adobe-GB1


✅ Summary (Windows fix):

Install Chinese fonts (SimSun, YaHei, Noto CJK).

Create/Edit xpdfrc.

Map fonts with displayFontTT.

Restart Xpdf.

------------------------------------------------
Method 2
Install Xpdf Language Support Package

Download the CJK (Chinese) language support files from Xpdf’s official site:
👉 https://www.xpdfreader.com/download.html

There are separate .zip packages for Simplified Chinese (xpdf-chinese-simplified) and Traditional Chinese (xpdf-chinese-traditional).

Extract the package into the same folder where you installed Xpdf (e.g. C:\xpdf\).

This will add preconfigured CMap, Unicode mapping, and sample font config files.

Edit or copy the provided xpdfrc file from that package into your Xpdf directory (or C:\Users\<YourName>\xpdfrc).

The package already has the correct entries like cidToUnicode and cMapDir.

You only need to adjust font paths if your fonts are in non-default places.

Make sure Chinese fonts are installed in Windows (SimSun, SimHei, or Microsoft YaHei are usually present by default).

If missing, install open-source fonts like Noto Sans CJK.

Restart Xpdf and test your PDF again.