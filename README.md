embark-iiif: IIIF templates for Embark
======================================

Intro
-----

This repo contains a few templates for exporting object data from Embark as [IIIF Presentation manifests](http://iiif.io/api/presentation/2.1). At the [Colby College Museum of Art](http://colby.edu/museum) we use these templates to power our deep-zoom multi-image viewer and a number of our back-end tools for supporting educational and curatorial work. You can see our implementation in the object detail pages of the CCMA's [collection web pages](http://www.colby.edu/museum/?s=).

Usage
-----

Drop the `.shtml` files in the `WebFolder` directory of your Embark WebKiosk instance. From there, use Embark's data template query URLs:
- For objects: `http://foo.bar/results.html?layout=iiif_imgs&recordType=objects_1&query=_ID=4`
- For portfolios: `http://foo.bar/results.html?layout=iiif_portfolio&recordType=objects_1&maximumRecords=9999&query=[portfolios]_ID=103`
- For an IIIF collection of all objects: `http://foo.bar/results.html?layout=iiif_collection&recordType=objects_1&maximumRecords=9999&query=_ID>1`
- `viewer.html` provides a really bare-bones instance of UniversalViewer with a drag 'n drop link, just put the url to a manifest in the `manifest` url parameter. 
- The CCMA uses these templates with an image server running [loris](https://github.com/loris-imageserver/loris) and static folders of manifests deployed and monitored with [a simple script](https://github.com/ColbyMuseum/manifeisty).


Known issues
------------
- The object template provides bad data (`999`) for canvas height and width. Mirador and UniversalViewer still read those manifests fine, but YMMV. 
- More of a static shim than an adapter: the templates won't produce valid manifests without some adapting. They expect images to have a particular suffix ("_cd.jpg"), its resource URLs are all in Colby's schema, etc.
