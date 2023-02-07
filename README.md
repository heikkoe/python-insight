# API client for Jira Assets

This is a API client to access data in the Jira Service Management Assets [JSM Assets](https://support.atlassian.com/jira-service-management-cloud/docs/manage-your-assets-and-configuration-items-with-insight/).

Api documentation:
 * https://developer.atlassian.com/cloud/assets/intro/introduction-and-basics/
 * https://developer.atlassian.com/cloud/assets/rest/api-group-aql/

## Usage

```python
from jira_insight import *


# Initialize the main Insight object with the URL and credentials for Basic Auth
insight = Insight("https://jira.example.com", ("USERNAME", "PASSWORD"))

# TODO: Build in or mention the retrieval of workspace id that is now mandatory
insight.insight_api_url = "https://api.atlassian.com/jsm/assets/workspace/{}/v1".format(workspaceId)

# Get a specific object schema by ID
object_schema = InsightObjectSchema(insight, 1)
# Search for objects by IQL
objects = object_schema.search_iql("SerialNumber = DEADBEEF")
```

## Caveats
* First and foremost: This is alpha software. I use it for a specific use case,
but for everything else, there be dragons.
* This is probably very slow with complex object schemas, as many things are
loaded preemptively when the Insight object is first instanciated.
* You can not yet edit objects after they have been created.
