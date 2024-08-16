---
layout: home
title: Critical AI @ MEPO 2024
nav_exclude: true
permalink: https://thicc-mepo-2024.github.io/
seo:
  type: Course
  name: PSU MEPO 2024 Critical AI learning
---

# Gaining a critical perspective on AI use during engineering processes

<div align="center" style="font-size: 11px;">

Work done by Dixon Zor and Chris Dancy as a part of [THiCC Lab](https://sites.psu.edu/thicc)
Funds towards this work were provided by [the National Science Foundation](https://www.nsf.gov/) through a [grant to Chris Dancy](https://news.engr.psu.edu/2023/dancy-christopher-nsf-career-award.aspx)

</div>

Welcome to this opportunity to use one of those mysterious AI tools to gain knowledge!

Here, we will focus on gaining a critical understanding of an ~~AI System~~ ~~generative AI System~~ large language model-based tool. 
Why the strike-outs in the previous sentence? Well, when we talk about _AI_ systems, that could mean **a lot** of different types of systems that are good for different purposes, so we will try to be specific and have you be critical enough when hearing of/engaging with AI systems that you remember to ask ciritcal questions:
- "What does 'AI' mean in this context?"
- "What are the limits of the use of a particular AI system in this context?"
- "What knowledge or information does the AI system use, or what data was used to train the AI system?"

Instead of blindly using an AI system because it "looks cool" or gives a "cool response", we want you to think more critically about it. We know you can stay cognizant and _stay ready_ to be critical and inquisitive, because you're engineers! If you've ever heard the phrase "debbie downer"...

<div align="center"><img src="imgs/debbie-downer.gif" width="350" style="border: 2px solid white"></div>

...well honestly that might be what you have to be sometimes. But thats the responsibility that can come with expertise!

## A little background

Unfortunately, many modern _AI_ systems are very opaque and the companies controlling those systems may make answering those questions very difficult. When we can't answer basic questions like those, it gives an opportunity for the **Critical Engineer** you should want to become to assess whether you want to use a particular system and whether it is the _responsible_ thing to do.

Values and context are important for thinking about _responsibility_ but folks like [Dr. Chris Dancy](https://sites.psu.edu/thicc/) and [Timnit Gebru](https://www.dair-institute.org/team/) (who's pictured below) have written quite a bit on perspectives of responsibility in using AI (and now _generative_ AI) systems. Give "[How to use generative AI more responsibly](https://www.nature.com/articles/s44159-024-00339-4.epdf?sharing_token=szDY0m4RQJYHkn3vH0CzKdRgN0jAjWel9jnR3ZoTv0Nkvzx9WwR5sRZDKMO5PrczGiPdY4IRpKwg2Kj776ZciQe0bPdzw2FSfuH7PC1CMgMSujOrsHH6w46kYojbTrjkWaVn5E0mXnpa95tc-hsbVVM-s1P_xhAU6rNUHLxJ_C0%3D) a quick read for one perspective on using generative systems responsibly (though this is slightly contextualized for psychologists and cognitive scientists, the majority of these lessons apply to engineers as well!)

<div align="center">
    <img src="imgs/gebru_DAIR.jpeg" height="300" style="border: 2px solid white" alt="Image of Timnit Gebru, founder of the Distributed AI Research Institute (DAIR)" />
    <div style="font-size: 11px;">
        After she was fired from Google Research as the co-lead (she led along with <a href="https://www.m-mitchell.com/">Margaret Mitchell</a>) of the AI Ethics group for her critical voice on company climate and the impacts of large language models (she was one of the authors of <a href="https://dl.acm.org/doi/10.1145/3442188.3445922">this famous paper</a>), Timnit Gebru founded the Distributed AI Research Institute (DAIR).
    </div>
</div>

This is all to say that as engineers, you will have a choice in what AI systems you use at tools and how you choose to use them! As folks who engineer artifacts you will likely want to be able to tinker and understand the systems you are using. Some AI systems make that easier than others.

### Large Language Models

<div align="center"><img src="imgs/Llama2_architecture.webp" width="350" style="border: 2px solid white"></div>

We are going to explore the use of one particular kind of _generative AI system_ called a large language model (LLM). Large language models are machine learning models that typically use a series of neural networks (with a particular _transformer_ architecture). Here large represents the number of parameters, which these days will be in the **billions** for the more popular LLMs. LLMs essentially output sequences of text (and sometimes other types of media) based on some input text. We'd note that they do not _understand_, they complete (text) sequences with an output. They do not have human-like cognitive processing of information, but these systems certainly _can_ output information that matches the input very well. The details aren't _too_ important for us, but if you want to learn more, there are both resources out there and classes here at Penn State that will cover some of the basics. Dr. Dancy spends a few classes going over the transformer architecture in his [AI, Humans, and Society class](https://cld5070.github.io/cmpsc497-fa23/), for example!

In this learning module, we are going to go over using a particular LLM, [LLaMa-2](https://llama.meta.com/llama2/). We chose Llama 2 for a few reasons, but two main reasons is **accessibility** of the model building code (particularly thanks to a platform called [Hugging Face](https://huggingface.co)) and **transparency** of the model (the creators of Llama 2 [give architecture detail as well as tell us what data the model was trained on](https://arxiv.org/abs/2307.09288)). Accessibility also means that more people can _tinker_ with the models to try to make it their own and fit within their own contexts, something that can be very powerful and impactful (responsible use & development is still important!)

These two points allow us to bring the model to you in the learning module in the way we do and that is much more open that popular systems such as chatGPT (which, beyond the company behind it not being transparent about how the model works or what data is was trained on, is implicated in [paying workers a very low wage for data work](https://time.com/6247678/openai-chatgpt-kenya-workers/) necessary for the models functioning.) The system we use is called Llama 2, which was released last year. While there has been a newer _version_ of the model released this year (Llama 3), the developers (Meta) hasn't yet released information on the data used to train the system, so we're sticking to this version for now. (Even version 2 works fairly well!)

The Llama 2 models come in three main variants: Llama 2 7B, Llama 2 13B, Llama 2 70B. Each number in those variants refers to the number of parameters. We will use the smallest of those models, Llama 2 7B. Why do we use the smallest version? (Take a second to think)

<div align="center">
<img src="imgs/thinking1.gif" width="350" style="border: 2px solid white"><br />
<img src="imgs/thinking2.webp" width="350" style="border: 2px solid white">
</div>

If you guessed because of how much space it takes up on a disk/hard drive, then you would be correct! But that's not the _only_ reason we would consider in computational system to use something _smaller_. If you also guessed because of how long it takes to run the model (i.e., speed), then you are also correct! 

When we say speed, we are specifically talking about how long it takes the model to give _output_ given some _input_, what we'd call an _inference_. This is because the amount of parameters basically tells us how many computational functions we'll need to run to eventually get to an output (we won't go into the math and architecture here) - typically the more parameter, the more computational functions we need to run.  

So in the normal chatbot example (and we'll be interfacing with a form of chatbot here soon) the input is what you right to the chatbot and the output is it's response. The other big aspect of speed related to these models (but which we don't have to worry about directly) is how long it takes to train the model.  If you go to the [model card](https://huggingface.co/docs/hub/model-cards#model-cards) for this [model on HuggingFace](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf), you'll run across the table shown below:

<div align="center"><img src="imgs/llama2_model-card.png" alt="Llama 2 model card"/></div>

The important take-away here is that training incurs a cost in time and in the amount of carbon emitted (read: _polution_), so the size of model you decide to train matters. While one instance of model inference, is much "cheaper" than training, you can imagine that inference actually ends up being where the most environmental impact occurs, with queries (input-output requests) from millions of users happen in a short amount of time. So, the smaller model you can use to accomplish a task, the less space, time, and environmental impact you will likely have.

**NOW** if you're asking, "well why are we even doing this, then?!? Can't we just not use the systems?"

Well, yes and no. _You_ can not use the systems, but there's a good chance you will given the ubiquity of these systems and when you do we want you to be able to think critically about that use. So we'll try to give you some knowledge and experience here, but leave it to you to gain the expertise you need throughout your educational journey. If nothing else, we're here to make your life more difficult so that you can't just do things out of ignorance.

<div align="center"><img src="imgs/sorry.webp" width="350" style="border: 2px solid white"/></div>

Now that we've given a high-level view of why we're doing this and a little background, let's move on to your MEPO, design challenge specifics.

## The design competition and using a chatbot

What we are going to do here is use the chatbot (that uses a Llama 2 model for output) in the way many folks are using it now - to find information and solutions to problems. We'll do this in a guided way that contetualizes _queries_ you'll give to the chatbot with your design challenge. Throughout this, you'll have an opportunity to see the code that is used to develop the chatbot system, or you might end up not worrying too much about the code itself and instead follow the minimum instructions to get input/output.

Either way, you'll have this module to refer back to later if you want! In showing you "how the sausage is made", we'll also show you some methods folks use to augment their models with specific context and information so that they work better.

<div align="center"><img src="imgs/science.gif" width="350" style="border: 2px solid white"/></div>

Ok, let's get to setting up our model and running things! Navigate to the `Chatbot_main.ipynb` file to begin!

<div align="center"><img src="imgs/letsdothis.gif" width="350" style="border: 2px solid white"/></div>
