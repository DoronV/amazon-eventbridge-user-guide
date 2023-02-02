# Delete an EventBridge scheduled rule using an AWS SDK<a name="example_eventbridge_DeleteRule_section"></a>

The following code examples show how to delete an Amazon EventBridge scheduled rule\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Java ]

**SDK for Java 2\.x**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javav2/example_code/eventbridge#readme)\. 
  

```
    public static void deleteEBRule(EventBridgeClient eventBrClient, String ruleName) {

        try {
            DisableRuleRequest disableRuleRequest = DisableRuleRequest.builder()
                .name(ruleName)
                .eventBusName("default")
                .build();

            eventBrClient.disableRule(disableRuleRequest);
            DeleteRuleRequest ruleRequest = DeleteRuleRequest.builder()
                .name(ruleName)
                .eventBusName("default")
                .build();

            eventBrClient.deleteRule(ruleRequest);
            System.out.println("Rule "+ruleName + " was successfully deleted!");

        } catch (EventBridgeException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
    }
```
+  For API details, see [DeleteRule](https://docs.aws.amazon.com/goto/SdkForJavaV2/eventbridge-2015-10-07/DeleteRule) in *AWS SDK for Java 2\.x API Reference*\. 

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/eventbridge#code-examples)\. 
  

```
suspend fun deleteEBRule(ruleName: String) {

    val request = DisableRuleRequest {
        name = ruleName
        eventBusName = "default"
    }

    EventBridgeClient { region = "us-west-2" }.use { eventBrClient ->
        eventBrClient.disableRule(request)
        val ruleRequest = DeleteRuleRequest {
            name = ruleName
            eventBusName = "default"
        }

        eventBrClient.deleteRule(ruleRequest)
        println("Rule $ruleName was successfully deleted!")
    }
}
```
+  For API details, see [DeleteRule](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation) in *AWS SDK for Kotlin API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using EventBridge with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.