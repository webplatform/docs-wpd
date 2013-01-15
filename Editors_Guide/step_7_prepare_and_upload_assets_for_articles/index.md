{{Page_Title|Editor's Guide: Step 7: Prepare and upload assets for articles}}
{{Flags}}
{{Summary_Section|This is Step 7 of the [[WPD:Editors_Guide|Editor's Guide]].}}
{{Basic Page}}
==Step 7. Prepare and upload assets for articles==
===Determine the ideal dimensions and quality settings for images===  
When adding images to an article, there are many factors to consider. Specifically, take the time to consider:

* The optimal dimensions of the image file (such as 300 pixels wide x 150 pixels high)
* The minimal acceptable quality of the image (which dictates the image's file size in KB) such as a JPG file set at 70% quality
* The shortest, most descriptive file name to use

You can prepare images before uploading them by using an image-editing program or online editing tool to open the master file or screenshot, save a copy of the file, and then make the following changes:

* Crop the image file. Images should only be as large as required to display the content to conveyed. 
* Resize the image file to a maximum width of 650 pixels. 

{{Note| If an image absolutely must be much larger than 650 pixels wide, create and upload a smaller thumbnail image, add a link to the thumbnail image on the page, and then link it to a full size image hosted somewhere else on the Web.}}

===Save image files with descriptive names===
After you make changes to the file's dimensions, you can use the image-editing program or online resource to save a copy of the file to your desktop. Avoid using generic file names, such as: image 04.png, screenshot.png, figure10.jpg, or code.jpg.

Name exported image files descriptively, like this:
* chrome_prefs.png
* box_model_diagram.png
* color_adjusted_landscape.jpg
* wiki_stewards_meeting.jpg

Only use underscores (not spaces, dashes, or other punctuation) when naming files to be uploaded. Also avoid capitalization and use all lower case characters.

===Optimize image quality===  
Using an image-editing program or online resource, you can crop, resize, and export the resulting image file to compress it for display in a browser. Since desktop and mobile screens have a resolution of 72 ppi (pixels per inch), there is no need to upload files that have a higher resolution; doing so simply takes up more space and causes the files to take longer to load.

When you export the edited file to create the version to be uploaded, you are usually presented with several compression options. Experiment with different file formats to determine which setting works best with your image's content. The goal is to create a PNG or JPG file with the smallest possible file size and minimal acceptable image quality, while ensuring that the dimensions (height and width) are just large enough to clearly see it. 

Follow these guidelines:

*If the image you are uploading contains simple content with solid colors and minimal details (like a flow chart or screenshot), it is usually best to save the file using the PNG 8 format. 

*If the image is photo-realistic, very detailed, or includes gradients, drop shadows, or continuous tones, (such as a digital  photograph), save the file using the JPEG format with 70% quality. 

===Online tools helpful for optimizing image files===
If you prefer, you can use an online image compression application (instead of using image-editing software installed on your machine) to edit, compress, and export optimized image files. Remember to save files with a maximum width of 650px. 

Some popular online image optimizers are:
* [http://www.pngoptimizer.com/ PNG Optimizer]
* [http://pixenate.com/ Pixenate]
* [http://pmt.sourceforge.net/pngcrush/ PNG Crush]

===Use the Upload File page to upload the images.===
After cropping, resizing, compressing, exporting, and renaming the image file, it is ready to be saved to your desktop. Once the file is ready to go and saved to your machine, the next step involves uploading it:

* Visit the [[http://docs.webplatform.org/wiki/Special:Upload Upload File page]
* Browse to select the optimized image file on your desktop
* Enter a short description that summarizes the uploaded file and its usage

{{Note| Please do not attempt to upload images that are several MB in file size to this wiki. Use an image-editing program or online image compression application to resize the image and create a smaller version. Reducing both the dimensions and quality of the image file will help you generate a smaller file size.}}

If you have questions about a file you are trying to upload, see Step 2 to learn how to ask for help online.

===Add the link to an uploaded image in the article draft===
After you have uploaded the file to the wiki site, the last step involves adding a link to the file in the page you are editing or creating.

* Enter the syntax to link the uploaded image file in the article, like this: 
&#91;&#91;Image:file_name.png|alt=Screenshot of the element rendered in Opera browser&#93;&#93;

The part of the syntax that actually adds the link to the page is: 

&#91;&#91;Image:file_name.png#93;&#93;

Read the section on accessibility below to learn about the alternate text added to every image file you link. 

{{Note| If you are linking to other file types (asset files other than images) in pages, use this syntax instead: 

&#91;&#91;File:file_name.png&#93;&#93;}}

===Make pages accessible: Add alternate text (Alt tags) to images===
When you add links to uploaded image files, it is very important to include alternate text in pages and articles. Alternate text is stored in the alt attribute of HTML image tags, and it is used to describe the visual content for screen readers. Alt tag text also displays in some browsers when a visitor hovers their cursor over an image - to offer a text description for the graphic.

To add alt text to images in Media Wiki, include the |alt=my alternate text  syntax.

For example, this line of code added to a page in the wiki:

&#91;&#91;Image:cssbasic.png|alt=Screenshot of the Opera browser showing an applied inline style sheet#93;&#93;

Is rendered by the browser as:

&#60;img src="cssbasic.png alt="Screenshot of the Opera browser showing an applied inline style sheet"&#62;


{{Notes_Section}}
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=