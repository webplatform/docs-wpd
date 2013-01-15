{{Page_Title|Editor's Guide: Step 7: Prepare and upload assets for articles}}
{{Flags}}
{{Summary_Section|This is Step 7 of the [[WPD:Editors_Guide|Editor's Guide]].}}
{{Basic Page}}
==Step 7. Prepare and upload assets for articles==

When adding images to an article, there are many factors to consider. Specifically, take the time to consider:

* The optimal dimensions of the image file (such as 300 pixels x 150 pixels)
* The minimal acceptable quality of the image (which dictates the image's file size in KB) such as a JPG file with 70% quality
* The shortest, most descriptive file name to use

You can prepare images before uploading them by using an image editing program to open the master file or screenshot, and then make the following changes:

* Crop the image file. Images should only be as large as required to display the content to conveyed. 
* Resize the image file to a maximum of 650 pixels wide. 

{{Note| If an image absolutely must be much larger than 650 pixels wide, create and upload a smaller thumbnail image, add a link to the thumbnail image on the page, and then link it to a full size image hosted somewhere else on the Web.}}

*Ensure accessibility of the images you upload and link, by adding alt text in articles to describe the visual content for screen readers.
* Please do not try to load images of several MB to this wiki! If the dimensions of an image exceed 650 pixels wide, use an image-editing program to resize the image and save a smaller version. See the following image optimization section below for more information. 

===Optimizing images===  
Using an image-editing program, you can crop, resize, and export the resulting image file to compress it for display in a browser. Since screens have a maximum resolution of 72 dpi, there is no need to upload files with a higher resolution; doing so simply takes up more space and causes files to take longer to load.

When you export the edited file to generate the version to be uploaded, you usually have several compression options available in the image-editing program. Experiment with different file formats to determine which setting works best with the image content. The goal is to create a PNG or JPG file with the smallest possible file size and acceptable quality, while ensuring that the image is large enough (height and width) to clearly see it. 

Follow these guidelines:

If the image you are uploading contains simple content with solid colors and minimal details (like a flow chart), it is usually best to save the file using the PNG 8 format. (Most image-editing programs offer this option in their export settings.) If the image is more detailed, such as a browser screenshot or photograph, save the file using the JPEG format with 70% quality. You can use an image compression application such as [[http://pmt.sourceforge.net/pngcrush/ PNG Crush]].</p></li>
* Save images with appropriate semantic file names. For example, use '''box-shadow-output.jpg''', rather than '''my-great-image.jpg''' or '''454654756-awesome.jpg'''.
* To add alt text to images in Media Wiki, you use the option alt=my alt text. So for example:

<pre>[[Image:cssbasic.png|alt=Screenshot of the Opera browser showing an applied inline style sheet]]</pre>

<p>Maps to</p>

<pre><img src="cssbasic.png alt="Screenshot of the Opera browser showing an applied inline style sheet"></pre>


===Optimize files.===
* Optimize PNG image files and resize to a maximum width of 650px. Some popular optimizers are:
** http://www.pngoptimizer.com/
***** [COMMENT:] This will require a new page. 
** http://pixenate.com/
===Name image file names descriptively.===
* Right: chrome_prefs.png, drop_shadow.png, box_model_diagram.png
* Wrong: image 04.png, screenshot.png, figure10.png, code.png
===Use the Upload File page to upload the images.===
* http://docs.webplatform.org/wiki/Special:Upload
===Add the link to an uploaded image in the article draft.===
* Enter the syntax to link the uploaded image file in the article: &#91;&#91;File:File.jpg&#93;&#93;
</div>
{{Notes_Section}}
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=