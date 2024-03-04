# Using Claude 3 Opus for video summarization

This is an attempt at Andrej Karpathy's video to course [challenge](https://twitter.com/karpathy/status/1760740503614836917)

The resulting model-generated course can be found [here](https://hundredblocks.github.io/transcription_demo/).

To produce it, we used a transcript of the video along with screencaps taken every few seconds. We then chunked it into N parts, and passed each part through the prompt below. No further editing was done.

Prompt
```


Human: Here is a transcript of a video, including screenshots at different timestamps.
The transcript was generated by an AI speech recognition tool and may contain some errors/infelicities.
Your task is to transform the transcript into an html blog.
The writing style of the blog, including desired balance between text and code is illustrated in a screenshot in <desired_writing_style>.
The visual style of the blog, including page layout, font, headings and image styles are described in <desired_visual_style>.

{transcript_with_name}
<desired_writing_style>
{desired_writing_style}
</desired_writing_style>
<desired_visual_style>
{desired_visual_style}
</desired_visual_style>

This transcript is noisy. Please rewrite it into an html format for an blog using the following guidelines:
- output valid html
- insert section headings and other formatting where appropriate
- use styling to make images, text, code, callouts and the page layout and margins look like the example in <desired_visual_style>
- remove any verbal tics
- if there are redundant pieces of information, only present it once
- rewrite conversational content in the style shown in <desired_writing_style>, including headings to make the narrative structure easier to follow along
- each transcript includes too many images, so you should only include the most important 1-2 images in your output
- choose images that provide illustrations that are relevant to the transcript
- prefer to include images which display complete code, rather than in progress
- when relevant transcribe important pieces of code and other valuable text
- if an image would help illustrate a part of a transcript, include it
- to include an image, insert a tag  with src="frames/hh_mm_ss.jpg"  (ie "frames/00_12_35.jpg") copying the exact image timestamp inserted above the image in the transcript
- add captions to images
- do not add any extraneous information: only include what is either mentioned in the transcript or the images

Your final output should be suitable for inclusion in a textbook.

Assistant: <!DOCTYPE html>
```
