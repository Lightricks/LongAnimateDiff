# LongAnimateDiff

[Sapir Weissbuch](https://github.com/SapirW), [Naomi Ken Korem](https://github.com/Naomi-Ken-Korem), [Daniel Shalem](https://github.com/dshalem), [Yoav HaCohen](https://github.com/yoavhacohen) | Lightricks Research

[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-yellow)](https://huggingface.co/spaces/Lightricks/LongAnimateDiff)

We are pleased to release the "LongAnimateDiff" model, which has been trained to generate videos with a variable frame count, 
ranging from 16 to 64 frames. 
This model is compatible with the original AnimateDiff model.

We release two models:
1. The LongAnimateDiff model, capable of generating videos with frame counts ranging from 16 to 64. You can download the weights from either
[Google Drive](https://drive.google.com/file/d/1rKvG7paObqPwke-9jqRMgH5cVZvWjIcj/view?usp=sharing) or [HuggingFace](https://huggingface.co/Lightricks/LongAnimateDiff). For optimal results, we recommend using a motion scale of 1.28.
2. A specialized model designed to generate 32-frame videos. This model typically produces higher quality videos compared to the LongAnimateDiff model supporting 16-64 frames. 
   Please download the weights from [Google Drive](https://drive.google.com/file/d/1ulrQuiGIJpK7lMvgdruF2Q2FJgHnj5_m/view?usp=sharing) or [HuggingFace](https://huggingface.co/Lightricks/LongAnimateDiff).
   For better results, use a motion scale of 1.15.

## Results

<table class="center">
            <tr style="line-height: 0">
            <td colspan="1" style="border: none; text-align: center">Walking astronaut on the moon</td>
            <td colspan="1" style="border: none; text-align: center">A corgi dog skying on skis down a snowy mountain</td>
            <td colspan="1" style="border: none; text-align: center">A pizza spinning inside a wood fired pizza oven</td>
            <td colspan="1" style="border: none; text-align: center">A young man is dancing in a Paris nice street</td>
            <td colspan="1" style="border: none; text-align: center">A ship in the ocean</td>
            <td colspan="1" style="border: none; text-align: center">A hamster is riding a bicycle on the road</td>
            </tr>
            <tr>
            <td style="border: none"><img src="assets/gifs/walking_astronaut_on_the_moon_48.gif"></td>
            <td style="border: none"><img src="assets/gifs/a_corgi_dog_skying_on_skis_down_a_snowy_mountain_48.gif"></td>
            <td style="border: none"><img src="assets/gifs/A_pizza_spinning_inside_a_wood_fired_pizza_oven.gif"></td>
              <td style="border: none"><img src="assets/gifs/a_young_man_is_dancing_in_a_paris_nice_street_48.gif"></td>
            <td style="border: none"><img src="assets/gifs/a_ship_in_the_ocean_48.gif"></td>
            <td style="border: none"><img src="assets/gifs/A_hamster_is_riding_a_bicycle_on_the_road_48.gif"></td>
            </tr>
            <tr style="line-height: 0">
            <td colspan="1" style="border: none; text-align: center">A drone is flying in the sky above a forest</td>
            <td colspan="1" style="border: none; text-align: center">A drone is flying in the sky above the mountains</td>
            <td colspan="1" style="border: none; text-align: center">A swan swims in the lake</td>
            <td colspan="1" style="border: none; text-align: center">A ginger woman in space future</td>
            <td colspan="1" style="border: none; text-align: center">Photo portrait of old lady with glasses</td>
            <td colspan="1" style="border: none; text-align: center">Small fish swimming in an aquarium</td>
            </tr>
            <tr>
            <td style="border: none"><img src="assets/gifs/a_drone_is_flying_in_the_sky_above_a_forest_32.gif"></td>
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
'AnimateDiff models' folder within your ComfyUI framework. You can run the graph bellow.

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