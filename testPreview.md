The context length for Ollama models can be set manually. By default, Ollama models have a context length of 4096 tokens, but some models can handle more. For example, the Mistral model can handle up to 32,000 tokens, but it only shows a 4,096 token limit in the model configuration page[1][4].

To modify the context length for an Ollama model, you can follow these steps:

1. **Retrieve the Model Configuration**:
   - Use the command `ollama show <model_name> --modelfile > conf.txt` to export the current configuration of the model into a file named `conf.txt`[2].

2. **Modify the Configuration File**:
   - Open `conf.txt` in a text editor and add a new line with the parameter for the context window size. For example, to set the context window to 8,192 tokens, add the line `PARAMETER num_ctx 8192`[2].

3. **Create a New Model with Updated Configuration**:
   - Run the command `ollama create <new_model_name> -f conf.txt` to create a new model based on the updated configuration[2].

Alternatively, you can also use the API to specify the context length. For example, using the `curl` command:
   ```bash
   curl http://localhost:11434/api/generate -d '{
       "model": "llama3-gradient",
       "prompt": "Why is the sky blue?",
       "options": {
           "num_ctx": 256000
       }
   }'
   ```
   Or using the CLI:
   ```bash
   ollama run llama3-gradient
   >>> /set parameter num_ctx 256000
   ```
   This sets the context window to 256,000 tokens[3].

These steps allow you to customize the context length for your Ollama models to better suit your specific needs and tasks.

Citations:
[1] https://github.com/enricoros/big-AGI/issues/495
[2] https://help.nurgo-software.com/article/202-optimizing-ollama-models-for-brainsoup
[3] https://ollama.com/library/llama3-gradient
[4] https://www.reddit.com/r/LocalLLaMA/comments/16oae0h/how_do_i_find_out_the_context_size_of_a_model/
[5] https://ollama.com/library/everythinglm
