# Your template

https://github.com/sullyo/prompt2ui
https://github.com/e2b-dev/e2b-cookbook/tree/main/examples/anthropic-power-artifacts

# Dependencies

- `newRepoFromTemplate(githubTemplateUrl)` => makes the repo
- `editGithubRepo(githubRepoUrl, files:[{path:"src/app/page.tsx", content: skeletonCodeString}])` => makes a pr to the repo and adds the file
- `deploy(githubRepoUrl)` => makes it a project on vercel
- `generateSdk(openapiUrl)` => wijnand makes it

# Spec

1. [b] `generateSkeleton` => `{skeletonCodeString, pagesJson}`
2. `generatePage(openapiUrl, page)` 
    - uses artifact system prompt 
    - gets partial openapi spec for operationIds (`pruneOpenapi`)
    - generates code for a page using the SDK
3. `generateEntireFrontend(openapiUrl)` => first runs `generateSkeleton` and then `generatePage` for every resulting page.

```ts
type Page = { filepath, pageComponentName,instructions,operationIds:string[] }
```

TODO: 

- parser that takes into account artifact type
- in a follow-up prompt based on the code string, openapi summary, and using JSON MODE, ask it to also respond with a JSON (of specified schema) that contains `Page[]`

