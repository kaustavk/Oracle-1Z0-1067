# Oracle-1Z0-1067                      <p>       </p>          <img src="imags/logo2.JPG" alt="logo2" style="zoom:25%;margin-right: auto" />

## Comprehensive cheat sheet to pass Oracle 1Z0-1067 Exam

------

### **Short Notes**

- If OCI Notifications service does not receive an acknowledgement from a subscription endpoint, the service **tries to redeliver messages for up to two hours**. 
- Configure an alarm on the NumberofNotificationFaiied metric through the OCI Monitoring service to help debug the issue
- Resource manager stacks are free but you are charged for the resources they create and the number of lines of text in your Terraform configuration files.

### <u>Console connections:</u>
- If you do not disconnect from the session, your serial console connection will automatically be terminated after 24 hours.
- VNC console connection uses SSH port forwarding to create a secure connection from your local system to the VNC server attached to your instance's console

### <u>OCI Ansible Modules:</u>
- OCI Ansible Modules represent discrete provisioning tasks or operations that you can invoke individually from the command line, or else run Individually or in sequence from a playbook.
- OCI Ansible Modules enable orchestrating, provisioning, and configuration management tasks on Oracle Cloud Infrastructure



------

### **Single Choice Answer**

------

- **Automate the provisioning of this new environment:** 
  OCI Resource Manager

- **Add the SSH key to your running Instance:**
  modify the serial console connection string to include the identity file flag, -I to specify the SSH key to use

- **key benefit of using Resource Manager for your Terraform provisioning and management activities:**
  Resource Manager manages the Terraform state file for your infrastructure and locks the file so that only one Job at a time can run on a given stack

- **Does NOT help you get the optimal performance out of the OCI File Storage service:**
  Serialize operations to the file system to access consecutive blocks as much as possible

- **Encryption of data in-transit:**
  Native Oracle Net Services encryption and integrity capabilities

- **Ensure that data being accessed by the application is encrypted:**
  Native Oracle Net Services encryption and integrity capabilities

- **Essential components of the Oracle Cloud Infrastructure Notifications service:**
  A topic with a name unique across the tenancy, a subscription, and a message where content is published

- **Application is NOT functioning properly:**
  Verify that the compute resource quota has not been exceeded

- **Make IPSec VPN connection highly available (HA):**
  Add another Customer-Premises Equipment (CPE) and create second IPSec VPN connection with the same Dynamic Routing Gateway (DRG)

- **Unable to access an internal application running behind Public Load Balancer using a compute instance pool with auto scaling enabled. Some deleted items In the Audit Log while troubleshooting.**
  The route table rules associated with the subnet within the VCN

- **Include a quota to allow for use of only 20 VM.Standard shapes per Availability Domain:**
  set compute quota vm-standard2-2-count to 20 in compartment dev

- **Control the costs and avoid any overspending:**
  Associate a Budget Tag to each resource with monthly budget amount and use that Information to prepare a weekly report to send to each team

- **NOT a valid technique to accurately attribute costs to resources used by each team:**
  Create an Identity and Access Management (IAM) group for each team. Create an OCI budget for each group to track spending

- **Make API calls to other services without storing credentials in a configuration file:**
  Create appropriate matching rules in the Dynamic Group to create an Instance Principal

- **Daily Incremental backups need to be retained for at least 50 days:**
  Enable automatic backups and choose the preset retention period of 60 days

- **Oracle allow as part of vulnerability and penetration tests testing:**
  Customers are allowed to use their own testing and monitoring tools

- **Develop an Ansible playbook to centralize configuration file management and deployment:** 
  <u>Download</u> the dynamic inventory script provided by Oracle Cloud Infrastructure and include It in the playbook Invocation command

- **Delete all the temporary data with /temp prefix:** 
  oci os object <u>bulk-delete</u> -ns vision -bn app-data --prefix /temp --force

- **Download the archive file as quickly as possible:**(get , 128)
  oci os object <u>get</u> -ns my-namespace -bn my-bucket --name my-large-object --multipart-download-threshold 2000 --part-size <u>128</u>

- **You want to restrict admin access to a specific region. E.g., PHX-Admlns:**
  Allow group PHX-Admins to manage all-resources in tenancy where request.region = 'phx'

- **Service error:NotAuthorizedOrNotFound. shape VM.Standard2.4 not found, http status code: 404:**
  terraform apply -auto-approve

- **metric query showing all read IOPS at a one-minute interval, filtered to this compartment and aggregated for the maximum:**
  IopsRead[lm]{compartmentId="ocidl.compartment.ocl.phx..exampleuniquelD"}.grouplng().max()

  

------

### Multiple - Choice Question & Answer

------

**Required parameters to launch an instance in Oracle Cloud:**

1. Virtual Cloud Network
2. subnet
3. Availability Domain
4. instance shape
5. image operating system

**TRUE for OCI Compute Service:**

1. You can launch a virtual or bare metal instance by using the same LaunchInstance API
2. You can share custom images across tenancies and regions

**Configured for a load balancer to accept incoming traffic:**

1. a listener
2. a back-end server
3. a back end set

**Two parameters are required in a back end set’s HTTP health check:**

1. Port
2. URL Path

**High Availability on Oracle Cloud Infrastructure:**

1. Configure your database to have Data Guard in another Availability Domain in Sync mode within a region.
2. Distribute your application servers across all Availability Domains within a region.

**Valid targets for creating a budget In OCI:**

1. Select Cost-Tracking Tags as the type of target for your budget.
2. Select Compartment as the type of target for your budget

**Copy of data in the destination region to use If a region-wide disaster occurs in the source region + Minimize costs:**

1. Backup block volumes. 
2. Copy block volume backups from source region to destination region at regular intervals

**Load historical data(25 MB -20 GB) stored in CSV text files to ADW:**

1. Create Auth token
2. Create an object storage credential by executing DBMS_CI OUD.CREATE _CREDENTIAL
3. Using OCI CLI upload the CSV files to an OCI object storage bucket.
4. Create the tables in the ADW database
5. Execute DBMS_CLOUD.COPY_DATA for each CSV file to copy the contents into the corresponding ADW database table

**True about the Bulk Export of OCI Audit Log Events:**

1. Exported logs are available in the object storage buckets in your tenancy.
2. Exported logs remain available indefinitely

**Identify excessive spend across all resources in your tenancy:**

1. Create a tag namespace named BILLING with a Tag Key named CostCenter. 
2. Tag each of your resources with this Tag Key and the correct value

**To manage alarms In OCI, which three actions can be performed through the OCI Console:**

1. View alarm history for last 3 months.
2. View all the firing alarms.
3. Move an alarm to a different compartment



------

### CLI Command Based Notes

------

**Manage multiple environments using OCI CLI:**
Use OCI CLI profiles to create multiple set of credentials in your config file, and reference the appropriate profile at runtime

**Lifecycle policy for object storage:**
oci os object-lifecycle-pollcy put -ns <object_storage_namespace> -bn <bucket_name> -Items<json_formatted_llfecycle_policy>

**Copy an object from Object Storage:**
oci os object copy --namespace-name <object_storage_namespace> --bucket-name <source_bucket_name> --source-object-name <source_object> --destination-namespace <destination_namespace_string> --destination-region <destination_region> --destination-bucket <destination_bucket_name> --destination-object-name <destination_object_name> 

**Provision new resources on OCI multiple times through CLI:** 
oci resource-manager stack <u>create --compartment-id</u> <compartment_OCID> --config-source prod.zip --variables file://variables.json --display-name "Production Stack build" --description "Creating new Production environment" 

**Command Line Interface to launch a Linux virtual machine fails. Which is invalid parameter:**
-t <tenancy_id>

------



#### Our Premium Practice Tests  Enrolment Link

------

**1Z0-1085:**
https://www.udemy.com/course/1z0-1085-20-oraclecloudinfrastructurefoundationsassociate

**1Z0-1067:**
https://www.udemy.com/course/oracle-cloud-infrastructure-cloud-operations-associate/

**1Z0-1072:**
https://www.udemy.com/course/1z0-1072-oracle-cloud-infra-architect-associate/

**1Z0-1084:**
https://www.udemy.com/course/oracle-cloud-infra-developer-2020-associate-practice-test/

**1Z0-931:**
https://www.udemy.com/course/oracle-autonomous-database-cloud-specialist-1z0-931-practice-test/

**1Z0-997:**
https://www.udemy.com/course/1z0-997-oracle-cloud-infrastructure-architect-professional-k



**Note:** For Active Coupon please contact us through below mail id 

------

**Contact Us:**

[digitechcloud20@gmail.com]



