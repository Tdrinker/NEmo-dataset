# NEmo
-- News That Triggers Emotion, an Affectively-Annotated Dataset of Gun Violence News

### data_10.json
Each news sample has at least 10 annotations for all three experiment
types (Text only, Image only, Text + Image). It is structured in the
following way:

```
{
    news title: {
        url,
        text_responses: [
            {
                emotion,
                intensity,
                feeling,
                reason,
                annotator_politics,
                annotator_media_time
            },
            .
            .
            .
        ],
        image_responses: [...]
        textimage_responses: [...]
    },
    .
    .
    .
}
```

where 
* `url` is the image url
* `text_responses` is the annotations for the Text only experiment type. Has at least 10 items.
    * `emotion` is the emotion chosen from the 8 emotional categories (Amusement, Awe Contentment, Excitement, Fear, Sadness, Anger)
    * `intensity` is the scale of that emotion from 0 to 10
    * `feeling` is the descriptive emotion of the annotator
    * `reason` is a descriptive paragraph that justifies `feeling`
    * `annotator_politics` is the political leaning of the annotator. Values 
      from {**LEFT**, **MODERATE**, **RIGHT**}
    * `annotator_media_time` is the average hours the annotator spend actively consuming news media on a given day. Values from {**none**, **less1** (less than 1 hour), **1to2**, **3to5**, **5More** (5 hours or more)}
* `image_responses` is the annotations for Image only experiment type. 
  Same structure as `text_responses`. Has at least 10 items.
* `textimage_responses` is the annotations for Text + Image experiment type. 
  Same structure as `text_responses`. Has at least 10 items.
  
### data_1.json
Each news sample has at least 1 annotations for all three experiment
types (Text only, Image only, Text + Image).

### data_all.json
All annotation data including news sample that has annotation for only 1 or 2 experiment types.
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
                },
                .
                .
                .
            ]
        },
        .
        .
        .
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
                },
                .
                .
                .
            ]
        },
        .
        .
        .
    },
    text_image: {
        news headline: {
            url
            responses: [
                {
                    emotion,
                    intensity,
                    feeling,
                    reason,
                    annotator_politics,
                    annotator_media_time
                },
                .
                .
                .
            ]
        },
        .
        .
        .
    },
}
```

where 
* `text-only`, `image-only`, `text_image` correspond to the three experiment types