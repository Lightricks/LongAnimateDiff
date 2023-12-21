# LongAnimateDiff

[Sapir Weissbuch](https://github.com/SapirW), [Naomi Ken Korem](https://github.com/Naomi-Ken-Korem), [Daniel Shalem](https://github.com/dshalem), [Yoav HaCohen](https://github.com/yoavhacohen) | Lightricks Research

[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-yellow)](https://huggingface.co/spaces/Lightricks/LongAnimateDiff)

We are pleased to release the "LongAnimateDiff" model, which has been trained to generate videos with a variable frame count, 
ranging from 16 to 64 frames. 
This model is compatible with the original AnimateDiff model.  For optimal results, we recommend using a motion scale of 1.15.

We release two models:
1. The LongAnimateDiff model, capable of generating videos with frame counts ranging from 16 to 64. You can download the weights from either
[Google Drive](https://drive.google.com/file/d/1rKvG7paObqPwke-9jqRMgH5cVZvWjIcj/view?usp=sharing) or [HuggingFace](https://huggingface.co/Lightricks/LongAnimateDiff).
2. A specialized model designed to generate 32-frame videos. This model typically produces higher quality videos compared to the LongAnimateDiff model supporting 16-64 frames. 
   Please download the weights from [Google Drive](https://drive.google.com/file/d/1ulrQuiGIJpK7lMvgdruF2Q2FJgHnj5_m/view?usp=sharing) or [HuggingFace](https://huggingface.co/Lightricks/LongAnimateDiff).

**Update: December 27, 2023**
- We are releasing version 1.1 of the LongAnimateDiff model, which generates better videos of 64 frames.

## Results

<table class="center">
            <tr style="line-height: 0">
            <td colspan="1" style="border: none; text-align: center">A young man is dancing in a party</td>
            <td colspan="1" style="border: none; text-align: center">A teddy bear is drawing a portrait</td>
            <td colspan="1" style="border: none; text-align: center">A hamster is riding an auto rickshaw</td>
            <td colspan="1" style="border: none; text-align: center">A swan swims in a lake</td>
            <td colspan="1" style="border: none; text-align: center">A young man is dancing in a paris nice street</td>
            <td colspan="1" style="border: none; text-align: center">A cat is sitting next to a wall</td>
            </tr>
            <tr>
            <td style="border: none"><img src="assets/gifs/a_young_man_is_dancing_in_a_party.gif"></td>
            <td style="border: none"><img src="assets/gifs/a_teddy_bear_is_drawing_a_portrait.gif"></td>
            <td style="border: none"><img src="assets/gifs/A_hamster_is_riding_an_autorickshaw.gif"></td>
            <td style="border: none"><img src="assets/gifs/A_swan_swims_in_the_lake.gif"></td>
            <td style="border: none"><img src="assets/gifs/a_young_man_is_dancing_in_a_paris_nice_street.gif"></td>
            <td style="border: none"><img src="assets/gifs/a_cat.gif"></td>
            </tr>
            <tr style="line-height: 0">
            <td colspan="1" style="border: none; text-align: center">A gorilla is eating a banana.gif</td>
            <td colspan="1" style="border: none; text-align: center">A drone is flying in the sky above the mountains</td>
            <td colspan="1" style="border: none; text-align: center">A swan swims in the lake</td>
            <td colspan="1" style="border: none; text-align: center">A ginger woman in space future</td>
            <td colspan="1" style="border: none; text-align: center">Photo portrait of old lady with glasses</td>
            <td colspan="1" style="border: none; text-align: center">Small fish swimming in an aquarium</td>
            </tr>
            <tr>
            <td style="border: none"><img src="assets/gifs/a_gorilla_is_eating_a_banana.gif"></td>
            <td style="border: none"><img src="assets/gifs/a_drone_is_flying_in_the_sky_above_the_mountains.gif"></td>
            <td style="border: none"><img src="assets/gifs/A_swan_swims_in_the_lake_32.gif"></td>
            <td style="border: none"><img src="assets/gifs/a_ginger_woman_in_space_future.gif"></td>
            <td style="border: none"><img src="assets/gifs/photo_portrait_of_old_lady_with_glasses_32.gif"></td>
            <td style="border: none"><img src="assets/gifs/small_fish_swimming_in_an_aquarium_32.gif"></td>
            </tr>
</table>


## Installation and Usage


### ComfyUI usage

You can run our models using the ComfyUI framework. The models can be conveniently placed in the 
'AnimateDiff models' folder within your ComfyUI framework. You can run the graph below.

![alt text](https://github.com/Lightricks/LongAnimateDiff/blob/main/assets/ComfyUI.png)

### AnimateDiff codebase usage

_Note: our models work better with motion scale > 1. Motion scale is not implemented in AnimteDiff git, thus using ComfyUI is recommended._
```
git clone https://github.com/guoyww/AnimateDiff.git
cd AnimateDiff
conda env create -f environment.yaml
conda activate animatediff
git clone https://github.com/Lightricks/LongAnimateDiff.git
bash download_bashscripts/5-RealisticVision.sh
``` 
- Download the model from [Google Drive](https://drive.google.com/file/d/1ulrQuiGIJpK7lMvgdruF2Q2FJgHnj5_m/view?usp=sharing) / [HuggingFace](https://huggingface.co/Lightricks/LongAnimateDiff) 
and place in ```models/Motion_Module```.
- Download sd-1-5 model from [HuggingFace](https://huggingface.co/runwayml/stable-diffusion-v1-5).

```
python -m scripts.animate --config LongAnimateDiff/configs/RealisticVision-32-animate.yaml --inference_config LongAnimateDiff/configs/long-inference.yaml --L 32 --pretrained_model_path {path to sd-1-5 base model}
```
To run the 64 frames model:
- Modify the temporal_position_encoding_max_len parameter in ```LongAnimateDiff/configs/long-inference.yaml``` to 128.
- Download the model from [Google Drive](https://drive.google.com/file/d/1rKvG7paObqPwke-9jqRMgH5cVZvWjIcj/view?usp=sharing) / [HuggingFace](https://huggingface.co/Lightricks/LongAnimateDiff) 
and place in ```models/Motion_Module```.
- Download epicRealismNaturalSin from [civit.ai](https://civitai.com/models/25694/epicrealism) to ```models/DreamBooth_LoRA/epicRealismNaturalSin.safetensors```.
```
python -m scripts.animate --config LongAnimateDiff/configs/EpicRealism-64-animate.yaml --inference_config LongAnimateDiff/configs/long-inference.yaml --L {select number from 32|48|64} --pretrained_model_path {path to sd-1-5 base model}
```

## Disclaimer
This project is released for academic use. We disclaim responsibility for user-generated content. Users are solely liable for their actions. The project contributors are not legally affiliated with, nor accountable for, users' behaviors. Use the generative model responsibly, adhering to ethical and legal standards.


## Acknowledgements
[https://github.com/guoyww/AnimateDiff](https://github.com/guoyww/AnimateDiff.git)