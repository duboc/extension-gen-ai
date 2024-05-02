# test mermaid2

```mermaid
graph LR
    subgraph Looker Extension
        subgraph Generative Explore
            user((User)) --> chooseExplore(Choose Explore)
            chooseExplore --> getMetadata(Get Metadata)
            getMetadata --> createPrompt(Create Prompt)
            createPrompt --> llmModel(LLM Model)
            llmModel --> returnExplore(Return Explore)
            returnExplore --> user
            user --> chooseVisualization(Choose Visualization)
            chooseVisualization --> addToDashboard(Add to Dashboard)
        end
        subgraph Generative Insights on Dashboards
            user --> chooseDashboard(Choose Dashboard)
            chooseDashboard --> getData(Get Data)
            getData --> createPrompt(Create Prompt)
            createPrompt --> llmModel
            llmModel --> returnInsights(Return Insights)
            returnInsights --> user
        end
    end
    subgraph GCP
        subgraph BQML Remote Models
            llmModel --> bqRemoteModel(BQ Remote Model)
            bqRemoteModel --> geminiProApi(Gemini-Pro API)
        end
        subgraph BQML Remote UDF with Vertex AI
            llmModel --> bqRemoteUdf(BQ Remote UDF)
            bqRemoteUdf --> cloudFunction(Cloud Function)
            cloudFunction --> vertexAiApi(Vertex AI API)
        end
        subgraph Custom Fine Tune Model (Optional)
            llmModel --> bqRemoteUdf
            bqRemoteUdf --> cloudFunction
            cloudFunction --> vertexAiFineTuneModel(Vertex AI Fine-Tune Model)
        end
    end
```
