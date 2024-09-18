:original_name: rms_05_0504.html

.. _rms_05_0504:

Example Functions (Python)
==========================

Example Function of Evaluations Triggered by Configuration Changes
------------------------------------------------------------------

Config will invoke a function like the following example when it detects a configuration change to a related resource.

.. code-block::

   import requests
   import http.client
   import time
   requests.packages.urllib3.disable_warnings()


   def get_policy_resource(domain_id, resource):
       return {
           "domain_id": domain_id,
           "region_id": resource.get("region_id"),
           "resource_id": resource.get("id"),
           "resource_name": resource.get("name"),
           "resource_provider": resource.get("provider"),
           "resource_type": resource.get("type")
       }


   '''
   The evaluation result of a rule will be either Compliant or NonCompliant.
   In this example, if the properties.status of a resource matches the specified ECSstatus, NonCompliant is returned. Otherwise, Compliant is returned.
   '''

   def evaluate_compliance(resource, parameter):
       if resource.get("properties").get("status") == parameter.get("ECSstatus").get("value"):
           return "NonCompliant"
       else:
           return "Compliant"


   def update_policy_state(token, domain_id, evaluation):
       endpoint = "https://rms.eu-de.otc.t-systems.com"
       url = "{}/v1/resource-manager/domains/{}/policy-states".format(endpoint, domain_id)
       return requests.put(
           url=url,
           headers={
               "X-Auth-Token": token
           },
           json=evaluation,
           verify=False,
       )


   def handler(event, context):
       resource = event.get("invoking_event", {})
       parameters = event.get("rule_parameter")
       compliance_state = evaluate_compliance(resource, parameters)

       requests = {
           "policy_resource": get_policy_resource(event.get("domain_id"), resource),
           "trigger_type": event.get("trigger_type"),
           "compliance_state": compliance_state,
           "policy_assignment_id": event.get("policy_assignment_id"),
           "policy_assignment_name": event.get("policy_assignment_name"),
           "function_urn": event.get("function_urn"),
           "evaluation_time": event.get("evaluation_time"),
           "evaluation_hash": event.get("evaluation_hash")
       }

       for retry in range(3):
           response = update_policy_state(context.getToken(), event.get("domain_id"), requests)
           if response.status_code == http.client.TOO_MANY_REQUESTS:
               print("TOO_MANY_REQUESTS: retry again")
               time.sleep(1)
           else:
               if response.status_code == http.client.OK:
                   print("Update policyState successfully.")
               else:
                   print("Failed to update policyState.")
                   print(response.json())
               break

Example Function for Evaluations Triggered by Periodic Execution
----------------------------------------------------------------

Config will invoke a function like the following example for a custom rule that is executed periodically.

.. code-block::

   import requests
   import http.client
   import time
   requests.packages.urllib3.disable_warnings()

   def get_policy_resource(domain_id, resource):
       return {
           "domain_id": domain_id,
           "region_id": resource.get("region_id"),
           "resource_id": resource.get("id"),
           "resource_name": resource.get("name"),
           "resource_provider": resource.get("provider"),
           "resource_type": resource.get("type")
       }

   '''
   The evaluation result of a rule will be either Compliant or NonCompliant.
   In this example, if ten or more ECSs are in the status of SHUTOFF, NonCompliant is returned. Otherwise, Compliant is returned.
   Here, the Config advanced query API is used. You can use related APIs of other services as needed.
   '''

   def evaluate_compliance(token, domain_id):
       endpoint = "https://rms.eu-de.otc.t-systems.com"
       url = "{}/v1/resource-manager/domains/{}/run-query".format(endpoint, domain_id)
       body = {"expression":"select count(*) as cnt from resources where provider = 'ecs' and type = 'cloudservers' and properties.status = 'SHUTOFF'"}
       r = requests.post(
           url=url,
           json=body,
           headers={
               "X-Auth-Token": token
           },
           verify=False,
       )
       # example {"query_info":{"select_fields":["cnt"]},"results":[{"cnt":0}]}
       print(r.json())
       cnt = r.json().get("results")[0].get("cnt")
       if cnt < 10:
           print(cnt,"Compliant")
           return "Compliant"
       else:
           print(cnt,"NonCompliant")
           return "NonCompliant"


   def update_policy_state(token, domain_id, evaluation):
       endpoint = "https://rms.eu-de.otc.t-systems.com
       url = "{}/v1/resource-manager/domains/{}/policy-states".format(endpoint, domain_id)
       return requests.put(
           url=url,
           headers={
               "X-Auth-Token": token
           },
           json=evaluation,
           verify=False,
       )

   def handler (event, context):
       resource = event.get("invoking_event", {})
       parameters = event.get("rule_parameter")
       if resource.get("name") != "Account":
           return
       compliance_state = evaluate_compliance(context.getToken(), event.get("domain_id"))

       requests = {
           "policy_resource": get_policy_resource(event.get("domain_id"), resource),
           "trigger_type": event.get("trigger_type"),
           "compliance_state": compliance_state,
           "policy_assignment_id": event.get("policy_assignment_id"),
           "policy_assignment_name": event.get("policy_assignment_name"),
           "function_urn": event.get("function_urn"),
           "evaluation_time": event.get("evaluation_time"),
           "evaluation_hash": event.get("evaluation_hash")
       }

       for retry in range(3):
           response = update_policy_state(context.getToken(), event.get("domain_id"), requests)
           if response.status_code == http.client.TOO_MANY_REQUESTS:
               print("TOO_MANY_REQUESTS: retry again")
               time.sleep(1)
           else:
               if response.status_code == http.client.OK:
                   print("Update policyState successfully.")
               else:
                   print("Failed to update policyState.")
                   print(response.json())
               break
