---
title: "Image Scale"
description: "Illustrate size range with image of known object"
---

# Image Scale 🖼️

Background picture handler illustrating range of size is implemented in function
`findImageScale()` in file `progress.cpp`.

To add a new picture: 
Reference to the new picture should be added in code in above mentioned function.
`imRec` record should be populated with appropriate info when given scope (like kilometers in below example) was reached—that is it already `has value`—and fits into defined *Size* range.

``` C
    if (sRec.inKm.has_value()) {
        // Km range
        float tSize = *sRec.inKm;
        // Display range
        if ((tSize > 10) and (tSize < 100)) {
            imRec.found = true;
            imRec.file = "ny_city.jpg";
            imRec.text = "of the order of a Big City's (like New York) size";
            // Size of an object (100%)
            imRec.scale = 20.f / tSize;
        }
    }
```

If the frame (structure) size is smaller then object from picture size (denoted as `imRec.scale`), the picture is proportionally enlarged; if there is greater—picture is reduced.

An image itself shall be uploaded to https://pcc21.com/upload/ site as GitHub is essentially not for binary object storage.
Each picture should have a corresponding `LICENSE_*.txt` file.  
To upload the image into the site a password is needed.
Please ask for it by e-mail an author (the e-mail is embedded in public key presented on author's site—pcc21.com) or during pull request.

During installation process all needed pictures are fetched by installator script and placed in proper place.
For this additionally a picture name should be added to table of pictures in `install.sh` script, see example below:

``` shell
images_from_store=("burj_khalifa.jpg" "ny_city.jpg" "new_picture.jpg")
```

