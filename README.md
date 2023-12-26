# Leetcode Intensive tutorial and study guide 
We leveraged cutting-edge tools to create an efficient and effective study aid for LeetCode users. Here's an overview of our technical stack and how each component contributes to the guide:

## Technical Stack:
- **llama-index**
  - Function: Enhances the filling of LeetCode questions through integration with OpenAI.
  - Usage:
    - Utilizes a low-cost embedding model to process large amounts of data.
    - Generates embedding vectors for each LeetCode question, providing a unique representation based on its content.
- **NetworkX**
  - Function: Optimizes the study path for learners.
  - Usage:
    - Constructs a low-cost spanning tree to understand the relationships between different problems.
    - Implements a Depth-First Search (DFS) algorithm to plan an effective study order, helping users to progress logically through related topics.
- **SciKit-Learn**
  - Function: Clusters LeetCode problems for tailored learning experiences.
  - Usage:
    - Applies machine learning algorithms to cluster knowledge based on the similarity of the embeddings.
    - Groups similar problems together, allowing users to focus on specific areas of study or difficulty levels.
- **Pydantic**
  - Function: Transforms unstructured data into a structured format.
  - Usage:
    - Converts unstructured LeetCode problem data into structured JSON format.
    - Ensures data integrity and facilitates easier manipulation and retrieval of problem information.
