---
layout: page
title: Tableau Reports
description: >
   This project is a demonstration of how to prototype a Retrieval-Augmented Generation (RAG) Assistant employing a suite of open-source technologies, frameworks and fine-tuned Large Language Models.
   It can be adapted to many other business-specific use cases.
img: 
importance: 1
category: work
giscus_comments: true
---

A RAG Assistant Prototype. The live app can be accessed at [arXiv Assistant](https://amrsherif.live/arxiv-assistant), and the source code is available on [GitHub](https://github.com/amr-sheriff/arxiv-assistant).

---

## Demo 🎥

The arXiv Assistant is a simple demo designed to help researchers and practitioners stay up-to-date with the latest advancements in various fields by retrieving, summarizing, and answering queries about research papers from arXiv.

The assistant can retrieve and select relevant research papers based on user-specified criteria such as submission/revision date, domain/category, and topic. Additionally, it can also answer questions about the papers and highlight key points.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
      <div class='tableauPlaceholder' id='viz1722841736713' style='position: relative'>
          <noscript>
              <a href='#'>
                  <img alt=' ' src='https://public.tableau.com/static/images/gm/gmv-dynamics/GMVDynamics/1_rss.png' style='border: none' />
              </a>
          </noscript>
          <object class='tableauViz' style='display:none;'>
              <param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' />
              <param name='embed_code_version' value='3' />
              <param name='site_root' value='' />
              <param name='name' value='gmv-dynamics/GMVDynamics' />
              <param name='tabs' value='yes' />
              <param name='toolbar' value='yes' />
              <param name='static_image' value='https://public.tableau.com/static/images/gm/gmv-dynamics/GMVDynamics/1.png' />
              <param name='animate_transition' value='yes' />
              <param name='display_static_image' value='yes' />
              <param name='display_spinner' value='yes' />
              <param name='display_overlay' value='yes' />
              <param name='display_count' value='yes' />
              <param name='language' value='en-US' />
          </object>
      </div>
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

<script type='text/javascript'>
    var divElement = document.getElementById('viz1722841736713');
    var vizElement = divElement.getElementsByTagName('object')[0];
    if (divElement.offsetWidth > 800) {
        vizElement.style.minWidth = '1366px';
        vizElement.style.maxWidth = '100%';
        vizElement.style.minHeight = '850px';
        vizElement.style.maxHeight = (divElement.offsetWidth * 0.75) + 'px';
    } else if (divElement.offsetWidth > 500) {
        vizElement.style.minWidth = '1366px';
        vizElement.style.maxWidth = '100%';
        vizElement.style.minHeight = '850px';
        vizElement.style.maxHeight = (divElement.offsetWidth * 0.75) + 'px';
    } else {
        vizElement.style.width = '100%';
        vizElement.style.minHeight = '1600px';
        vizElement.style.maxHeight = (divElement.offsetWidth * 1.77) + 'px';
    }
    var scriptElement = document.createElement('script');
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>


## Development Process 🛠️

The development process involved leveraging state-of-the-art techniques to implement a lightweight yet efficient LLM system. Key technologies used include:
- [**Instruction Tuning Dataset**](https://huggingface.co/datasets/amrachraf/arXiv-full-text-synthetic-instruct-tune): Generate domain-specific synthetic dataset consisting of instructions and QAs pairs.
- **QLoRA Quantization**: For efficient memory usage.
- **Parameter-Efficient Fine-Tuning (PEFT)**: Utilizing LoRA adapters. PEFT mdel available [here](https://huggingface.co/amrachraf/arxiv-assistant-merged_peft_model).
- **Function Calling and In-Context Learning**: To enhance the assistant's capabilities.
- **Retrieval Augmented Generation (RAG) process**: To improve contextual understanding and relevance, which enhances the retrieval and generation process.
- **vLLM**: As the serving and inference engine.
- **HuggingFace Text Embedding Inference**: Serving the embedding model using HuggingFace to provide high-quality embeddings for document retrieval and processing.

### Key Features ✨

- **Retrieve and Summarize Papers**: Quickly find and get summaries of the latest research papers.
- **Answer Queries**: Get answers to specific questions about research papers.
- **Web-Based UI**: Built with Chainlit for an interactive user experience.
- **Observability Functionality**: Supported by Literal AI, providing insights and monitoring for the assistant's performance and operations.
- **In-Chat Memory**: Allows the assistant to remember previous interactions within a session.
- **Resume Chat Capability**: Enables users to continue previous chat sessions seamlessly.
- **Chain of Thought Visualization**: Supported by Literal AI, providing an intuitive understanding of the assistant's reasoning process.
- **Data persistence & human feedback**: Ensures that the data is retained and allows for continuous improvement through user feedback.

### Integrations & Frameworks 🔌

- [**Weights & Biases**](https://wandb.ai/site): For monitoring and logging the fine-tuning process.
- [**LangChain**](https://www.langchain.com/): For implementing retrieval and processing modules.
- [**HuggingFace TEI**](https://huggingface.co/docs/text-embeddings-inference/en/index): For text embedding inference, serving high-quality embeddings.
- [**vLLM**](https://github.com/vllm-project/vllm): As the serving and inference engine.
- [**Chainlit**](https://github.com/Chainlit/chainlit/tree/main): to build scalable conversational AI or agentic applications.
- [**Literal AI**](https://literalai.com/): LLM evaluation and observability platform

## Quickstart Guide ⚡

To get started with arXiv Assistant, open the terminal and follow these steps:

1. **Clone the Repository**:
   ```bash
   $ git clone https://github.com/your-repo/arxiv-assistant.git
   $ cd arxiv-assistant
   ```

2. **Create a `.env` file in the root directory with the following environment variables:**
   ```bash
   $ nano .env
   ```
   ```env
   LITERAL_API_KEY=<your-literal-api-key>
   VLLM_API_KEY=<your-vllm-server-key>
   CHAINLIT_AUTH_SECRET=<your-chainlit-auth-secret>
   OAUTH_GOOGLE_CLIENT_ID=<your-oauth-google-client-id>
   OAUTH_GOOGLE_CLIENT_SECRET=<your-oauth-google-client-secret>
   HF=<your-huggingface-token>
   EMBED_ENDPOINT=<your-tei-endpoint>
   VLLM_ENDPOINT=<your-vllm-server-endpoint>
   MAX_ARXIV_CHAR=<max-character-to-load-from-each-arxiv-document>  # set to None to disable
   ```

3. **Build docker image**:
   ```bash
   $ docker build -t arxiv-assistant:latest .
   ```

4. **Run countainer**:
   ```bash
   $ docker run -d --env-file .env -p 8080:8080 arxiv_assistant:latest
   ```

Run the app locally and navigate to [localhost:8080/arxiv-assistant](http://localhost:8080/arxiv-assistant) 🥂

## License 📜
This project is licensed under the [Apache 2.0](https://github.com/amr-sheriff/arxiv-assistant/blob/main/LICENSE) license.
