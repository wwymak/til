# Config for videos in label studio

At the moment, the example in label studio for video classification is not very clear. If you want a proper video 
embedded in the labelling interface, and your videos come from e.g. GCS, then you have to define you config like so:

```
<View>
  
  <Header value="For each video, choose whether it is blocking or not"></Header>
  <HyperText name="video" value="$html"/>
  <Choices name="type" toName="video" choice="single-radio">
    <Choice value="blocking" />
    <Choice value="NOT blocking" />
  </Choices>
</View>

```

(under settings)

Then, in the cloudsync settings, under 
`File filter by regex, example: .* (If not specified, all files will be skipped)`, use `.*.json`

Finally, for each video in the GCS bucket, define one json file per video like so:
```json
{"html": "<video src='gs://BUCKET_NAME/path/to/video/VIDEO_NAME.mp4' controls>"}

```