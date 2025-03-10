CircularNet is a waste analysis system that combines computer vision and machine
learning to optimize recycling processes. To implement CircularNet, you need
these key components:

-  **Machine vision camera:** A specialized camera captures high-resolution
   images of materials on the conveyor belt, ensuring consistent quality even
   with fast-moving waste. While CircularNet can process images from various
   sources, such as cell phones or GoPro cameras, a machine vision camera with a
   global shutter is recommended for optimal results with moving objects.
-  **Computational unit:** The image analysis component contains the trained ML
   models that perform the analysis. The computational unit can be one of the
   following:

    -  An **edge device** for on-site, real-time processing.
    -  A **cloud-based solution** for scalable, remote processing.
    -  **Your own server** for complete control over the infrastructure.

-  **Machine Learning (ML) models:** These pre-trained models are the heart of
   CircularNet. They use a mask-based image analysis algorithm to identify and
   classify materials and their forms within the waste stream.
-  **Reporting dashboard:** The raw images and analysis results are compiled and
   presented through a visual dashboard. This dashboard provides detailed
   breakdowns of materials, classifications, and other insights, empowering you
   to make data-driven decisions to improve sorting and recycling processes.

You can stream results to a dashboard on various cloud platforms or your own
server. This guide provides instructions specifically for deploying a dashboard
on Google Cloud.

## Training models

CircularNet's machine learning models utilize a vision-based masking algorithm
to identify and classify diverse materials within waste streams. These models
have been pre-trained using images from various Material Recovery Facilities
(MRFs), representing multiple waste compositions.

While the pre-trained models are ready for use, you can refine their performance
by continuing the training process. Retraining can help you improve performance
on specific material types or adapt to unique waste stream characteristics in
your geography or deployment area. Retraining involves gathering and annotating
additional images from three primary sources:

-  **MRF images**: Images captured and labeled directly from conveyor belts at
   MRFs.
-  **Google's internal annotation**: Images annotated by Google's dedicated
   team.
-  **Automatic annotation**: A processing script automatically annotates images
   of sorted materials, focusing on common types like PET, aluminum cans, and
   cardboard boxes.

The automatic annotation process involves the following tasks:

-  Generating masks for objects in the images, using either bounding boxes or
   more precise mask detection depending on the image complexity.
-  Filtering and cleaning the generated masks to remove duplicates or errors.
-  Adding annotations to create the final training dataset.

![A model applies mask detection to an image containing aluminum cans passing on a conveyor belt.](/images/mask-detection.png)

**Figure 1.** A model applies mask detection to an image containing aluminum
cans passing on a conveyor belt.

After preparing the data, the ML models are taught and trained with it to learn
how to identify materials in new real-world scenarios.

## Applying the models to your data

Once your machine vision camera has captured images or videos of your waste
stream, you can put CircularNet's models to work. Upload these captured files to
a server where CircularNet analyzes each image or video frame. The models
leverage their learned knowledge to identify and classify the various materials
and their forms present in the waste stream. Models can analyze data in
real-time or in batches, depending on your needs and chosen deployment
constraints. The analysis results, including details about each detected object,
such as material type and form, are then systematically organized and stored in
a [BigQuery](https://cloud.google.com/bigquery) database table. This structured
data fuels the [Looker](https://cloud.google.com/looker) dashboard, where you
can access and visualize it through comprehensive reports and insightful
visualizations. The reporting dashboard serves as your gateway to insights
generated by CircularNet, allowing you to create customized reports and
empowering you to make data-driven decisions that enhance the efficiency and
effectiveness of your sorting and recycling operations.

## What's next

-  [Learn more about the deployment solutions that CircularNet offers](/official/projects/waste_identification_ml/circularnet-docs/content/solutions/).
-  [Set up a hardware solution for your needs](/official/projects/waste_identification_ml/circularnet-docs/content/system-req/).
-  [Learn how to deploy CircularNet on Google Cloud or an edge device](/official/projects/waste_identification_ml/circularnet-docs/content/deploy-cn/).
-  [Learn how to prepare your data and use the models to analyze images](/official/projects/waste_identification_ml/circularnet-docs/content/analyze-data/).
-  [Learn more about the visual dashboard to get analytics and reports](/official/projects/waste_identification_ml/circularnet-docs/content/view-data/).