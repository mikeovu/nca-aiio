# Unit 3: Generating Images Using Generative AI (demo)

**Exam mapping:** Topic 1, *Essential AI Knowledge*
**Source:** AI Infrastructure and Operations Fundamentals course, demo video transcript

## What this demo covers
A hands-on walkthrough of making and editing images from text prompts with a model hosted on **ai.nvidia.com**. It's light on theory, but it defines the **image-generation parameters** you should be able to recognize.

---

## 1. Where the models live
- **ai.nvidia.com** → **Try Now** shows models grouped by application and industry (gaming, healthcare and so on). Image models are under **Visual Design**.
- Models differ in what they do:
  - most turn **text into 2D images**
  - some turn **text into 3D models**
  - some turn **a single image into a short video**
- Each model has **its own set of parameters**.
- The demo model is **Getty Images**, which makes **high-resolution 4K images**. It was **trained on NVIDIA's Edify platform** using Getty Images' library (Edify is the diffusion model from Unit 3).

## 2. Model features

| Feature | What it does |
|---|---|
| **Text to Image** | Generates a 2D image from a text prompt. This model accepts **up to 50 words** |
| **Inpainting** | Changes **part of an existing image** using a **mask** plus a text prompt |
| **Outpainting** | Extends or changes an input image using a prompt and a mask |

By default, one run returns **4 images** within seconds.

## 3. Parameters to know

| Parameter | What it controls | Key detail |
|---|---|---|
| **Prompt** | What to generate | **More descriptive gives closer results.** E.g. "landscape" → "…with mountains and a river" → "…snow-covered… wooden cabin by the river" |
| **Negative prompt** | What **not** to generate | E.g. enter "cloud" to keep clouds out |
| **Seed** | The **starting point** of the random generation process. A whole number from 0 up | **Same seed + same prompt = the same image.** A different seed gives different images. Use it to **make variations while keeping other aspects fixed** |
| **Media type** | Photography vs. illustration | Switches the output style |
| **Aspect ratio** | Image dimensions | E.g. 1:1 vs. 16:9 |
| **Prompt weight** | **How closely the model follows the prompt** | **Low = more creative. High = follows the prompt exactly.** **7.5 is a good balance.** At 1, images drifted: a missing cabin, a lake instead of a river, clouds coming back |

> Why seeds matter: generation **involves randomness**, so the same prompt can give different images each run. A fixed seed makes the output **reproducible**.

## 4. Inpainting walkthrough
1. Choose **Inpainting** and select an input image (the demo uses a smartphone with a blank screen).
2. **Add New Mask** and paint over the area to change. A brush size slider controls precision (15 was used).
3. Enter a prompt (the earlier landscape prompt) and **Run**. Only the **masked area**, the phone screen, is replaced.

## 5. Tips for better prompts
- Be **as specific as possible** and use **descriptive adjectives**.
- **Combine several elements** to build complex scenes.
- Use **negative prompts** to leave out unwanted elements.
- Try different **styles and perspectives**.
- Think about **lighting, colors and composition**.
- **Reference existing images or artwork** for guidance.
- **Break complex scenes** into smaller prompts.
- **Iterate and refine** based on what you get.

---

## Key Terms
- [**Text to image**](https://build.nvidia.com/explore/visual-design): generating an image from a written prompt.
- **Negative prompt**: words describing what the image should *not* contain.
- **Seed**: the number that sets the starting point of the random generation. Fixing it makes results reproducible.
- **Prompt weight**: how closely output sticks to the prompt, traded off against creativity.
- **Inpainting / outpainting**: editing an existing image within a **mask**, guided by a prompt.
- **Mask**: the painted region that marks which part of the image to change.

## Exam Tips
- **Seed = reproducibility.** The same seed and prompt give the same image.
- **Prompt weight: low means creative, high means literal.** About **7.5** balances the two.
- **Negative prompts exclude content.** **Inpainting needs a mask.**
- The Getty Images model was **trained on NVIDIA Edify** and outputs **4K** images.

---

## NVIDIA Documentation
Official NVIDIA pages for this lesson's main concepts (links checked November 10, 2026).

- [Visual Design models on build.nvidia.com](https://build.nvidia.com/explore/visual-design): where the demo's image-generation models live.
- [Try NVIDIA NIM APIs](https://build.nvidia.com/): the hosted model catalog the demo starts from.
