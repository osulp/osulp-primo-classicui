# primo

HTML and CSS files for Primo/1Search. These files live at http://primo.library.oregonstate.edu

Primo Sandbox: http://alliance-primo-sb.hosted.exlibrisgroup.com/primo_library/libweb/action/search.do?vid=OSU 
<br/>Primo Production: http://alliance-primo.hosted.exlibrisgroup.com/primo_library/libweb/action/search.do?vid=OSU

## CSS

`osu.css` was added to the CSS mapping tables, so we no longer have to use Primo's File Uploader Utility. **Primo Home > Advanced Configuration > All Mapping Tables > CSS** The URL for this file is appended to the existing Primo CSS. The full value will look something like: `Primo_default.3.0.css;../uploaded_files/OSU/osu.css;http://primo.library.oregonstate.edu/osu.css`


## Sidebar Custom Tile

`sidebar.html` is pulled in as osuSidebar using a Custom Tile. 

### LibraryH3lp Chat Box

Most control of this widget happens in the LibraryH3lp administration area.


## Primo Alma Mashup Styling

Within Primo, when you click certain tabs (Item Details, Availability & Request Options, etc.) Alma 'mashups' are loaded into internal frames. These load Alma data with CSS separate from Primo, using a 'branding skin' ZIP file containing CSS and icon image files.

These files are in the `branding_skin` folder (the important one being `branding_skin/css/mashup.css`). To upload to Alma, they need to be zipped up into a file called **skin.zip** with all of the files and folder structure intact. The upload location in Alma is **General Configuration > Configuration Menu > Branding/Logo > Delivery System Skins**

Initial configuration is required to tell Primo to use this Alma skin in the delivery tabs.  To change those settings in the Primo Back Office, go to **General > Mapping Tables > Delivery**, then filter the Mapping table rows by Code `Alma*it` so that *Almagetit* and *Almaviewit* are among the lines displayed.  For both *Almagetit* and *Almaviewit* the end corresponding entry in the Template Code column will have the skin name:

```{{alma_base}}...&req.skin=OSU_summit_request_form```

Change the `req.skin=` parameter to match the name of your skin you uploaded to Alma (or add the parameter if it is missing).

## Testing

Changes to HTML files usually appear right away. Changes to CSS files can take several minutes to appear. Sometimes opening a different browser or running a new search query will force a reload of the CSS file.

### Test Javascript/jQuery on Sandbox only

```javascript
// Looks at URL for existence of 'alliance-pubsb'
if (document.location.href.indexOf('alliance-pubsb') > -1 ) {
  document.writeln("sandbox");
}
```


