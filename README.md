*embark-iiif: IIIF templates for Embark*

**Intro**
This repo contains a few templates for exporting object data from Embark as [IIIF Presentation manifests](http://iiif.io/api/presentation/2.1). At the [Colby College Museum of Art](http://colby.edu/museum) we use these templates to power our deep-zoom multi-image viewer and a number of our back-end tools for supporting educational and curatorial work.

**Usage**
Drop the `.shtml` files in the `WebFolder` directory of your Embark WebKiosk instance. From there, use Embark's data templates. From there, use the standard XML Data Sharing template query URLs:
- For objects: `http://foo.bar/results.html?layout=iiif_imgs&recordType=objects_1&query=_ID=4`
- For portfolios: `http://foo.bar/results.html?layout=iiif_portfolio&recordType=objects_1&maximumRecords=9999&query=[portfolios]_ID=103`
- For an IIIF collection of all objects: `http://foo.bar/results.html?layout=iiif_collection&recordType=objects_1&maximumRecords=9999&query=_ID>1

**Known Issues**
- The object template provides bad data (`999`) for canvas height and width. The WebKiosk supports a 4D tag that provides this information (as of 9.5.7), but the CCMA's IIIF implementation does not.
- Image filenames follow the CCMA's schema (that is, all hi-res images end in "_cd.jpg"). You'll want to change the templates to reflect your institution's file name schema.