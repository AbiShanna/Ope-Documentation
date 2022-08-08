# &nbsp; s2i to build application image

The s2i cli tool can be used to build application image from the builder image and application code.

1. Install s2i tool:
<br/> &nbsp; &nbsp;&nbsp; *sudo yum install source-to-image*
2. Pre-requisites - builder image, application code repo

3. Build the application image:

	&nbsp; &nbsp; &nbsp; &nbsp; *s2i build <application_source_code> <builder_image> <label_new_app_img>*

	&nbsp; &nbsp; - If the s2i scripts (assemble, run) are not available in the image, copy the scripts to local and provide the path like:
	
	&nbsp; &nbsp; &nbsp; &nbsp; *s2i build https://github.com/jappavoo/UndertheCovers quay.io/opeffort/ope_book:stable quay.io/opeffort/under_the_covers:stable --scripts-url=file://.s2i/bin*
