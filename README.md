# Evaluation Benchmark Standard

The Evaluation Benchmark Standard (EBS) is a proposed standardized format for representing and organizing evaluation benchmarks for Large Language Models (LLMs) and Artificial Intelligence (AI) systems.

The goal of this standard is to simplify the process of comparing and assessing the performance of various AI models across a wide range of tasks, such as embeddings, classifications, generation, hallucinations, multimodal, and more.

## Motivation

Currently, there are numerous evaluation benchmarks available for LLMs and AI systems, each with its own unique implementation and format.

This lack of standardization makes it difficult to compare the performance of different models and requires significant effort to adapt to each benchmark's specific requirements.

The Evaluation Benchmark Standard aims to address these issues by providing a unified format for representing evaluation benchmarks, making it easier to evaluate and compare AI models consistently.

## Key Features

- Standardized format: The EBS defines a standardized format for representing evaluation benchmarks, ensuring consistency and ease of use across different benchmarks and AI models.
- Centralized repository: A centralized repository will be created to store and manage the standardized evaluation benchmarks, providing a single source of truth for accessing and utilizing these benchmarks.
- Flexibility and extensibility: While the EBS provides a standardized format, it allows individual evaluation benchmark projects to implement their own code and logic, ensuring flexibility and customization.
- Simple integration: AI models and LLMs can easily integrate with the EBS by implementing a simple `.evalbench.json` file that adheres to the standardized format.
- Comprehensive coverage: The EBS aims to cover a wide range of tasks, including embeddings, classifications, generation, hallucinations, multimodal, and more, providing a comprehensive evaluation framework for AI models.

## Examples

Here are a few examples of how the Evaluation Benchmark Standard can be applied:

### Embedding Evaluation

```js
{
  "evals": [{
    "name": "Word Embedding Similarity (English)",
    "description": "Evaluates the quality of word embeddings by measuring the cosine similarity between word pairs.",
    "languages": [
      "en"
    ],
    // The task type and description: what does the benchmark evaluate specifically?
    "task": {
      "type": "embedding",
      "description": "Evaluates the quality of word embeddings by measuring the cosine similarity between word pairs."
    },
    // The results of the benchmark (metrics and/or data)
    "results": [
      {
        // Model: required; Refer to the model name in the models section
        "model": "my-embedding-model",
        // The below fields are arbitrarily defined, but should be consistent across all results
        "word1": "cat",
        "word2": "dog",
        "similarity": 0.8,
        "vector1": [], // optional; for example, the vector representation of the first word
        "vector2": [] // optional; for example, the vector representation of the second word
        // Other arbitrary fields...
      },
      // ...
    ],
    // Map column names to their corresponding data types and descriptions
    "results_mappings": [
      {
        "name": "Word 1",
        "column": "word1",
        "format": "text",
        "description": "The first word in the pair."
      },
      {
        "name": "Word 2",
        "column": "word2",
        "format": "text",
        "description": "The second word in the pair."
      },
      {
        "name": "Similarity Score",
        "column": "similarity",
        "format": "number",
        "description": "The cosine similarity score between the two words."
      }
    ],
    "models": [
      {
        "name": "my-embedding-model",
        "description": "My model description",
        "urls": [
          {
            "url": "https://huggingface.com/...",
          },
          // Other URLs...
        ]
      }
    ],
    "aggregates": [
      {
        "name": "Mean Similarity",
        "description": "Calculates the mean similarity score across all word pairs.",
        "column": "similarity",
        "value": "mean"
      }
    ],
  }]
}
```

### Text Classification Evaluation

```js
{
  "evals": [{
    "name": "Text Classification",
    "description": "Evaluates the quality of text classification models by measuring the precision, recall, and F1 score.",
    "languages": [
      "en"
    ],
    "task": {
      "type": "classification",
      "description": "Evaluates the quality of text classification models by measuring the precision, recall, and F1 score."
    },
    "results": [
      {
        // Model: required; Refer to the model name in the models section
        "model": "my-classification-model",
        // The below fields are arbitrarily defined, but should be consistent across all results
        "label": "positive",
        "expected_label": "positive",
        "text": "<The classified text.>", // optional; for example, the text that was classified
        "confidence": 0.8,
        // Other arbitrary fields...
      },
      // ...
    ],
    "results_mappings": [
      {
        "name": "Label",
        "column": "label",
        "format": "text",
        "description": "The true label of the text.",
        "in": ["positive", "negative", "neutral", "other"]
      },
      {
        "name": "Expected Label",
        "column": "expected_label",
        "format": "text",
        "description": "The expected label of the text.",
        "in": ["positive", "negative", "neutral", "other"]
      },
      {
        "name": "Confidence",
        "column": "confidence",
        "format": "number",
        "description": "The confidence score of the model's prediction.",
      }
    ],
    "models": [
      {
        "name": "my-classification-model",
        "description": "My model description",
        "urls": [
          {
            "url": "https://huggingface.com/...",
          },
          // Other URLs...
        ]
      }
    ],
    "aggregates": [
      {
        "name": "Mean Precision",
        "description": "Calculates the mean precision score across all labels.",
        "column": "score",
        "value": "mean"
      }
    ],
  }]
}
```

## Roadmap

To successfully implement the Evaluation Benchmark Standard, the following steps need to be taken:

1. Define the standardized format: Collaborate with the AI community to define a comprehensive and flexible format for representing evaluation benchmarks.
2. Engage with benchmark providers: Reach out to existing evaluation benchmark providers and encourage them to adopt the standardized format.
3. Build tooling and documentation: Develop tools and documentation to facilitate the creation, submission, and utilization of standardized evaluation benchmarks.
4. Foster community adoption: Promote the Evaluation Benchmark Standard within the AI community and encourage widespread adoption.

## Conclusion

The Evaluation Benchmark Standard aims to revolutionize the way AI models are evaluated and compared by providing a standardized format for representing evaluation benchmarks. By simplifying the process of benchmarking and enabling consistent comparisons across different models, the EBS will accelerate the development and advancement of AI technologies. We welcome contributions and feedback from the AI community to make this standard a reality.
