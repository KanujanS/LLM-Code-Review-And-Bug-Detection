# LLM-code-review-and-bug-detection
A container GitHub Action to review a pull request by HuggingFace's LLM Model.

If the size of a pull request is over the maximum chunk size of the HuggingFace API, the Action will split the pull request into multiple chunks and generate review comments for each chunk.
And then the Action summarizes the review comments and posts a review comment to the pull request.

## Pre-requisites
We have to set a GitHub Actions secret `HUGGING_FACE_API_KEY` to use the HuggingFace API so that we securely pass it to the Action.

## Inputs

- `apiKey`: The HuggingFace API key to access the API.
- `githubToken`: The GitHub token to access the GitHub API.
- `githubRepository`: The GitHub repository to post a review comment.
- `githubPullRequestNumber`: The GitHub pull request number to post a review comment.
- `gitCommitHash`: The git commit hash to post a review comment.
- `pullRequestDiff`: The diff of the pull request to generate a review comment.
- `pullRequestDiffChunkSize`: The chunk size of the diff of the pull request to generate a review comment.
- `repoId`: LLM repository id on HuggingFace.
- `temperature`: The temperature to generate a review comment.
- `topP`: The top_p to generate a review comment.
- `topK`: The top_k to generate a review comment.
- `maxNewTokens`: The max_tokens to generate a review comment.
- `logLevel`: The log level to print logs.

As you might know, a model of HuggingFace has limitation of the maximum number of input tokens.
So we have to split the diff of a pull request into multiple chunks, if the size of the diff is over the limitation.
We can tune the chunk size based on the model we use.

