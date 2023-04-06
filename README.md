# NEmo: An Affective Dataset of Gun Violence News
**Carley Reardon, Sejin Paik, Ge Gao, Meet Parekh, Yangling Zhao, Lei Guo, Margrit Betke, Derry Wijaya**

Boston University

{reardonc, sejin, ggao02, meet09, lingzhao, guolei, betke, wijaya}@bu.edu

* Note that we have an updated version of BU-NEmo+ which can be found here: https://github.com/Tdrinker/BU-NEmo-Plus. 

## Abstract
Given our society’s increased exposure to multimedia formats on social media platforms, efforts to understand how digital content impacts people’s emotions are burgeoning. As such, we introduce a U.S. gun violence news dataset that contains news headline and image pairings from 840 news articles with 15K high-quality, crowdsourced annotations on emotional responses to the news pairings. We created three experimental conditions for the annotation process: two with a single modality (headline or image only), and one multimodal (headline and image together). In contrast to prior works on affectively-annotated data, our dataset includes annotations on the dominant emotion experienced with the content, the intensity of the selected emotion and an open-ended, written component. By collecting annotations on different modalities of the same news content pairings, we explore the relationship between image and text influence on human emotional response. We offer initial analysis on our dataset, showing the nuanced affective differences that appear due to modality and individual factors such as political leaning and media consumption habits. Our dataset is made publicly available to facilitate future research in affective computing.

**Keywords:** affective computing, multimodal news data, crowdsourcing, language resources

## Data
NEmo is a multimodal affective dataset of gun violence news content extended from the Gun Violence Framing Corpus (GVFC) proposed by Liu et. al (2019) and Tourni et. al (2021). This dataset includes corresponding news headlines and lead images (which we will refer to as a news set) from gun violence-related articles annotated with three types of affective annotations:
1. the emotion the annotator feels from looking at the content, out of the following 8 classes (Amusement, Awe, Contentment, Excitement, Fear, Sadness, Anger, Disgust)
2. the intensity of the annotator's emotional response, on a scale from 1-5 (5 being the most intense)
3. a free-text written response explaining their emotional response, structured as "I feel <feeling> because <reason>"
    
We also collect these annotations in three experimental conditions:
1. only the headline of a given news set was presented to the annotators (Text Only)
2. only the lead image of a given news set was presented to the annotators (Image Only)
3. both the headline and image of a given news set were presented to the annotaors (Text & Image)
    
By comparing the annotations across these three conditions, we are able model the relationship between news modality & emotional response.
    
### GVFC Data
In order to use our annotations, you will need to download the text and image data we extend from GVFC. The GVFC text data and documentation can be found at the following address: https://derrywijaya.github.io/GVFC.html

Please note that GVFC includes journalistic news framing annotations. We have not used these in our data due to imbalance of these annotations among the set of news we have selected to annotate, but we believe they could bring very interesting insights in future work.
    
In order to access the corresponding images, please contact Dr. Derry Wijaya at wijaya@bu.edu
    
### NEmo Annotations
We offer three files of our annotations depending on the level of quality & cohesiveness you require for your work.
- data_10.json has the annotations for all news sets that have been annotated by *at least 10 people* in *all three experimental conditions*
- data_1.json has the annotations for all news sets that have been annotated by *at least 1 person* in *all three experimental conditions*
- data_all.json has the annotations for all news sets that have been annotated by *at least 1 person* in *any of the three experimental conditions*
    
We describe the schema of the files below:

#### data_10.json and data_1.json
These files have similar schema since they both have an annotation in all three experiments. These files are structured in the
following way:

```
{
    news headline: {
        url,
        text_responses: [
            {
                emotion,
                intensity,
                feeling,
                reason,
                annotator_politics,
                annotator_media_time
            }, ...
        ],
        image_responses: [...]
        textimage_responses: [...]
    }, ...
}
```

where 
* `news headline` corresponds to the headline of a given news set, which functions as a key
* `url` is the image url we used. The original image id from GVFC can be found in the file name in the url (i.e. ".../<image id>.jpg")
* `text_responses` is the annotations for the Text only experimental condition. This as at least 10 items in data_10.json, and at least 1 item in data_1.json.
    * `emotion` is the emotion chosen from the 8 emotional categories (Amusement, Awe Contentment, Excitement, Fear, Sadness, Anger)
    * `intensity` is the scale of that emotion from 1 to 5
    * `feeling` is the written emotion of the annotator (i.e. "I feel <feeling>")
    * `reason` is the written response that justifies `feeling` (i.e. "I feel <feeling> because <reason>")
    * `annotator_politics` is the political leaning of the annotator. Values 
      from {**LEFT**, **MODERATE**, **RIGHT**}
    * `annotator_media_time` is the average hours the annotator spends actively consuming news media on a given day. Values from {**none**, **less1** (less than 1 hour), **1to2**, **3to5**, **5More** (5 hours or more)}
* `image_responses` is the annotations for Image only experimental condition. 
  Same structure as `text_responses`. This as at least 10 items in data_10.json, and at least 1 item in data_1.json.
* `textimage_responses` is the annotations for Text & Image experimental condition. 
  Same structure as `text_responses`. This as at least 10 items in data_10.json, and at least 1 item in data_1.json.

#### data_all.json
This file schema is different due to not every news set having annotations in all three experimental conditions.
It is structured in the following way:
```
{
    text-only: {
        news headline: {
            responses: [
                {
                    emotion,
                    intensity,
                    feeling,
                    reason,
                    annotator_politics,
                    annotator_media_time
                }, ...
            ]
        }, ...
    },
    image-only: {
        image url: {
            responses: [
                {
                    emotion,
                    intensity,
                    feeling,
                    reason,
                    annotator_politics,
                    annotator_media_time
                }, ...
            ]
        }, ...
    },
    text_image: {
        news headline: {
            url,
            responses: [
                {
                    emotion,
                    intensity,
                    feeling,
                    reason,
                    annotator_politics,
                    annotator_media_time
                }, ...
            ]
        }, ...
    },
}
```

where 
* `text-only`, `image-only`, `text_image` correspond to the three experimental conditions. The corresponding news set can be identified either by the `news headline` key, or by the `image url` key, which corresponds to the image id in GVFC in the same way as `url` described above.
* all other variables are the same as in data_10.json and data_1.json

## Acknowledgement
This material is based upon work partially supported by the National Science Foundation under Grant No. 1838193. Any opinions, findings, and conclusions or recommendations expressed in this material are those of the authors and do not necessarily reflect the views of the National Science Foundation.

