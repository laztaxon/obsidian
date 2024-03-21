# The Dawn of LMMs

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/static/images/article4.6bc1851654a0.png)

## Metadata
- Author: [[Microsoft Corporation - Zhengyuan Yang∗, Linjie Li∗, Kevin Lin∗, Jianfeng Wang∗, Chung-Ching Lin∗, Zicheng Liu, Lijuan Wang∗]]
- Full Title: The Dawn of LMMs
- Category: #articles
- Document Note: The article discusses the capabilities of GPT-4V, a language model that can understand and process a mix of input images, sub-images, texts, scene texts, and visual pointers, and perform various vision and vision-language tasks. It can also understand and follow text instructions, recognize spatial relationships between objects in images, comprehend and generate descriptions in multilingual scenarios, and recognize scene text. The article also introduces the concept of visual referring prompting, a new method to interact with GPT-4V using visual markers drawn on input images.
- Summary: The article discusses the capabilities of GPT-4V, a language model that can understand and process a mix of input images, sub-images, texts, scene texts, and visual pointers, and perform various vision and vision-language tasks. It can also understand and follow text instructions, recognize spatial relationships between objects in images, comprehend and generate descriptions in multilingual scenarios, and recognize scene text. The article also introduces the concept of visual referring prompting, a new method to interact with GPT-4V using visual markers drawn on input images.
- URL: https://readwise.io/reader/document_raw_content/99487354

## Highlights
- Abstract
  Large multimodal models (LMMs) extend large language models (LLMs) with multi-sensory skills, such as visual understanding, to achieve stronger generic intelligence. In this paper, we analyze the latest model, GPT-4V(ision) [99–101, 1]1, to deepen the understanding of LMMs. The analysis focuses on the intriguing tasks that GPT-4V can perform, containing test samples to probe the quality and genericity of GPT-4V’s capabilities, its supported inputs and working modes, and the effective ways to prompt the model. In our approach to exploring GPT-4V, we curate and organize a collection of carefully designed qualitative samples spanning a variety of domains and tasks. Observations from these samples demonstrate that GPT-4V’s unprecedented ability in processing arbitrarily interleaved multimodal inputs and the genericity of its capabilities together make GPT-4V a powerful multimodal generalist system. Furthermore, GPT-4V’s unique capability of understanding visual markers drawn on input images can give rise to new humancomputer interaction methods such as visual referring prompting. We conclude the report with in-depth discussions on the emerging application scenarios and the future research directions for GPT-4V-based systems. We hope that this preliminary exploration will inspire future research on the next-generation multimodal task formulation, new ways to exploit and enhance LMMs to solve real-world problems, and gaining better understanding of multimodal foundation models. Finally, we acknowledge that the model under our study is solely the product of OpenAI’s innovative work, and they should be fully credited for its development. Please see the GPT-4V contributions paper [101] for the authorship and credit attribution: https://cdn.openai.com/contributions/gpt-4v.pdf. ([View Highlight](https://read.readwise.io/read/01hcmgtzjt0b586h922x2xfs3k))
- 1.1 Motivation and Overview ([View Highlight](https://read.readwise.io/read/01hcmgxqwfxy7nx0jrc20mtge2))
- In this paper, we report our preliminary explorations with (an early version of) GPT-4V, a state-of-the-art LMM with vision, built based on the SOTA LLM and trained with a large scale of multimodal data.
  Our exploration of GPT-4V is guided by the following questions.
  1. What are GPT-4V’s supported inputs and working modes? The genericity of multimodal models inevitably requires the system to work with the arbitrary mix of different input modalities. GPT-4V shows unprecedented ability in understanding and processing an arbitrary mix of input images, sub-images, texts, scene texts, and visual pointers. We also demonstrate that GPT-4V well supports the test-time techniques observed in LLMs, including instruction following [102], chain-of-thoughts [136, 66], in-context few-shot learning [23], etc.
  2. What are the quality and genericity ofGPT-4V’s capabilities on different domains and tasks? We sample queries covering a wide range of domains and tasks to understand GPT-4V’s capabilities, including open-world visual understanding, visual description, multimodal knowledge, commonsense, scene text understanding, document reasoning, coding, temporal reasoning, abstract reasoning, emotion understanding, and many more. GPT-4V shows impressive human-level capabilities across many of the experimented domains.
  3. What are effective ways to use and prompt GPT-4V? GPT-4V is strong in understanding pixel space edits, such as visual pointers and scene texts drawn on input images. Inspired by this capability, we discuss the “visual referring prompting” that directly edits input images to instruct the task of interest. Visual referring prompting can be seamlessly used together with other image and text prompts, presenting a nuanced interface for instruction and example demonstrations.
  4. What are promising future directions? Given GPT-4V’s strong capability across domains and tasks, we ask what is the next step for multimodal learning, and more broadly for artificial intelligence. We organize our thoughts and explorations into two perspectives, i.e., emergent novel application scenarios to focus on, and the future research directions for GPT-4V-based systems. We present our preliminary explorations to inspire future studies. ([View Highlight](https://read.readwise.io/read/01hcmgybc27fdy99w6jhg4gnte))
- 1.2 Our Approach in Exploring GPT-4V ([View Highlight](https://read.readwise.io/read/01hcmgzjta13qfj460fz2dbvep))
- the image captioning outputs of LMMs are much richer and contain more detailed descriptions than the ground truths in the image captioning benchmark datasets [27]. There is also a lack of public information regarding GPT-4V’s large-scale pre-training, which may violate the train-test setup for certain existing datasets and invalidate those benchmark numbers. Because of this, restricting the evaluation to existing benchmarks and metrics may unintentionally narrow the scope of GPT-4V’s assessment. Developing a comprehensive list of next-generation evaluation tasks and benchmarks would be the ideal ultimate solution. However, we left those as future work due to the significant efforts required.
  In lieu of quantitative benchmarking, this paper focuses on using qualitative results to provide a glimpse of GPT-4V’s new capabilities and potential emerging use cases. Our goal is to discover and preview what GPT-4V might already be capable of, even though these novel capabilities may not yet be entirely reliable. We hope this collection of explorations will inspire future research in establishing quantitative benchmarks for next-generation multimodal tasks, modernizing existing benchmarks, further improving model performance and system reliability, and sparkling innovation in emerging use cases. Following this, we will delve into the core designs for our approach to exploring GPT-4V.
  Sample selection guidance. This report focuses on presenting qualitative results to showcase the potential capabilities of GPT-4V, rather than providing comprehensive quantitative benchmark results. This naturally raises the question of the reliability of the showcased examples. The examples featured in this report may require careful instruction tuning to amplify GPT-4V’s corresponding capabilities. It should be noted that some complex cases may only work with the specifically designed prompts. As such, the capabilities demonstrated may not consistently work across different samples. Instead of showing only the reliable functionalities, the primary objective of this report is to provide readers with a list of our discovered potential capabilities of GPT-4V, which might otherwise be overlooked after a few unsuccessful trials.
  Sample selection to prevent mere memorizing from training. A fundamental design consideration in qualitative reports [24] is discerning models’ true capabilities from merely memorizing responses from training samples or making educated guesses based on hints from instructions and in-context examples. We carefully control both the images and text in the input prompts to prevent them from being seen during GPT-4V training. We generate original text queries from scratch, and try to use images that are either not accessible online or with a timestamp beyond April 2023. We will indicate instances where a specific sample does not meet this criterion, e.g., deliberately using samples from specific vision-language datasets. Beyond ensuring that samples are unseen, we incorporate rationale queries into the process. These queries are designed to probe the model’s reasoning process, thereby validating GPT-4V’s possession of the intended capability.
  The default working mode. As later detailed in Section 3, GPT-4V works effectively in different working modes, including zero-shot learning with instructions, in-context few-shot learning, etc. Among them, this report primarily focuses on zero-shot instruction tuning, as opposed to in-context few-shot learning. This design is to prevent potential information leakage from in-context examples. While in-context few-shot examples can enhance performance and reliability, they do not consistently engender new capabilities. As such, we designate zero-shot as the default working mode for presentation, and reduce the use of in-context examples to minimize examples’ impacts on the assessed capabilities. ([View Highlight](https://read.readwise.io/read/01hcmh2rxbwc40ewgmjzqdqs1m))
- 1.3 How to Read this Report?
  We give an overview of the report, structured around the four core questions that guide our exploration.
  1. What are GPT-4V’s supported inputs and working modes? Section 2 summarizes GPT-4V’s supported inputs and presents an overview of their corresponding use cases. Based on the flexible interleaved image-text inputs, Section 3 discusses GPT-4V’s different working modes, such as instruction tuning, in-context learning, and other emergent usages. ([View Highlight](https://read.readwise.io/read/01hcmh5v364vw5af90acf6rqzz))
- The section covers the novel ways of using and prompting GPT-4V, aiming to provide a comprehensive overview of how we will use GPT-4V in subsequent sections.
  2. What are the quality and genericity ofGPT-4V’s capabilities on different domains and tasks? The exploration of this question makes up a large portion of the report. Section 4 provides a comprehensive analysis covering a wide range of vision and vision-language scenarios, including image description and recognition on different domains, dense visual understanding, multimodal knowledge, commonsense, scene text understanding, document reasoning, and many more. We also separate out several novel and interesting capabilities. Section 6 studies GPT-4V’s capability in temporal, motion, and video understanding. Section 7 explores the abstract visual understanding and reasoning capability, and Section 8 covers the emotion and sentiment understanding.
  3. What are effective ways to use and prompt GPT-4V? We start the discussion on this question from the working mode and prompting method introduction in Section 3. In Section 5, we highlight one novel promoting technique, namely visual referring prompting, which draws visual pointers and scene texts on input images to prompt GPT-4V. We demonstrate the flexible prompting methods, such as the combination of instruction and example demonstrations, throughout the report in the given examples.
  4. What are promising future directions? Section 9 focuses on the novel use cases facilitated by GPT-4V. We hope these initial examples could inspire future works to design new task setups and present rigorous benchmarks. Section 10 imagines powerful future systems that can be built based on GPT-4V, such as the multimodal plugins, multimodal ([View Highlight](https://read.readwise.io/read/01hcmh67r8m9mfp4d2sp5akv83))