---
editable: false

__system: {"dislikeVariants":["No answer to my question","Recomendations didn't help","The content doesn't match title","Other"]}
---


# DiskService

A set of methods for managing Disk resources.

| Call | Description |
| --- | --- |
| [Get](#Get) | Returns the specified Disk resource. |
| [List](#List) | Retrieves the list of Disk resources in the specified folder. |
| [Create](#Create) | Creates a disk in the specified folder. |
| [Update](#Update) | Updates the specified disk. |
| [Delete](#Delete) | Deletes the specified disk. |
| [ListOperations](#ListOperations) | Lists operations for the specified disk. |

## Calls DiskService {#calls}

## Get {#Get}

Returns the specified Disk resource. <br>To get the list of available Disk resources, make a [List](#List) request.

**rpc Get ([GetDiskRequest](#GetDiskRequest)) returns ([Disk](#Disk))**

### GetDiskRequest {#GetDiskRequest}

Field | Description
--- | ---
disk_id | **string**<br>Required. ID of the Disk resource to return. To get the disk ID use a [DiskService.List](#List) request. The maximum string length in characters is 50.


### Disk {#Disk}

Field | Description
--- | ---
id | **string**<br>ID of the disk. 
folder_id | **string**<br>ID of the folder that the disk belongs to. 
created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br> 
name | **string**<br>Name of the disk. 1-63 characters long. 
description | **string**<br>Description of the disk. 0-256 characters long. 
labels | **map<string,string>**<br>Resource labels as `key:value` pairs. Maximum of 64 per resource. 
type_id | **string**<br>ID of the disk type. 
zone_id | **string**<br>ID of the availability zone where the disk resides. 
size | **int64**<br>Size of the disk, specified in bytes. 
block_size | **int64**<br>Block size of the disk, specifiedin bytes. 
product_ids[] | **string**<br>License IDs that indicate which licenses are attached to this resource. License IDs are used to calculate additional charges for the use of the virtual machine. <br>The correct license ID is generated by Yandex.Cloud. IDs are inherited by new resources created from this resource. <br>If you know the license IDs, specify them when you create the image. For example, if you create a disk image using a third-party utility and load it into Yandex Object Storage, the license IDs will be lost. You can specify them in the [yandex.cloud.compute.v1.ImageService.Create](/docs/compute/api-ref/grpc/image_service#Create) request. 
status | enum **Status**<br>Current status of the disk. <ul><li>`CREATING`: Disk is being created.</li><li>`READY`: Disk is ready to use.</li><li>`ERROR`: Disk encountered a problem and cannot operate.</li><li>`DELETING`: Disk is being deleted.</li><ul/>
source | **oneof:** `source_image_id` or `source_snapshot_id`<br>
&nbsp;&nbsp;source_image_id | **string**<br>ID of the image that was used for disk creation. 
&nbsp;&nbsp;source_snapshot_id | **string**<br>ID of the snapshot that was used for disk creation. 
instance_ids[] | **string**<br>Array of instances to which the disk is attached. 
disk_placement_policy | **[DiskPlacementPolicy](#DiskPlacementPolicy)**<br>Placement policy configuration. 


### DiskPlacementPolicy {#DiskPlacementPolicy}

Field | Description
--- | ---
placement_group_id | **string**<br>Placement group ID. 


## List {#List}

Retrieves the list of Disk resources in the specified folder.

**rpc List ([ListDisksRequest](#ListDisksRequest)) returns ([ListDisksResponse](#ListDisksResponse))**

### ListDisksRequest {#ListDisksRequest}

Field | Description
--- | ---
folder_id | **string**<br>Required. ID of the folder to list disks in. To get the folder ID use a [yandex.cloud.resourcemanager.v1.FolderService.List](/docs/resource-manager/api-ref/grpc/folder_service#List) request. The maximum string length in characters is 50.
page_size | **int64**<br>The maximum number of results per page to return. If the number of available results is larger than `page_size`, the service returns a [ListDisksResponse.next_page_token](#ListDisksResponse) that can be used to get the next page of results in subsequent list requests. The maximum value is 1000.
page_token | **string**<br>Page token. To get the next page of results, set `page_token` to the [ListDisksResponse.next_page_token](#ListDisksResponse) returned by a previous list request. The maximum string length in characters is 100.
filter | **string**<br><ol><li>The field name. Currently you can use filtering only on the [Disk.name](#Disk1) field. </li><li>An operator. Can be either `=` or `!=` for single values, `IN` or `NOT IN` for lists of values. </li><li>The value. Must be 3-63 characters long and match the regular expression `^[a-z]([-a-z0-9]{,61}[a-z0-9])?$`.</li></ol> The maximum string length in characters is 1000.


### ListDisksResponse {#ListDisksResponse}

Field | Description
--- | ---
disks[] | **[Disk](#Disk1)**<br>List of Disk resources. 
next_page_token | **string**<br>This token allows you to get the next page of results for list requests. If the number of results is larger than [ListDisksRequest.page_size](#ListDisksRequest), use the `next_page_token` as the value for the [ListDisksRequest.page_token](#ListDisksRequest) query parameter in the next list request. Each subsequent list request will have its own `next_page_token` to continue paging through the results. 


### Disk {#Disk1}

Field | Description
--- | ---
id | **string**<br>ID of the disk. 
folder_id | **string**<br>ID of the folder that the disk belongs to. 
created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br> 
name | **string**<br>Name of the disk. 1-63 characters long. 
description | **string**<br>Description of the disk. 0-256 characters long. 
labels | **map<string,string>**<br>Resource labels as `key:value` pairs. Maximum of 64 per resource. 
type_id | **string**<br>ID of the disk type. 
zone_id | **string**<br>ID of the availability zone where the disk resides. 
size | **int64**<br>Size of the disk, specified in bytes. 
block_size | **int64**<br>Block size of the disk, specifiedin bytes. 
product_ids[] | **string**<br>License IDs that indicate which licenses are attached to this resource. License IDs are used to calculate additional charges for the use of the virtual machine. <br>The correct license ID is generated by Yandex.Cloud. IDs are inherited by new resources created from this resource. <br>If you know the license IDs, specify them when you create the image. For example, if you create a disk image using a third-party utility and load it into Yandex Object Storage, the license IDs will be lost. You can specify them in the [yandex.cloud.compute.v1.ImageService.Create](/docs/compute/api-ref/grpc/image_service#Create) request. 
status | enum **Status**<br>Current status of the disk. <ul><li>`CREATING`: Disk is being created.</li><li>`READY`: Disk is ready to use.</li><li>`ERROR`: Disk encountered a problem and cannot operate.</li><li>`DELETING`: Disk is being deleted.</li><ul/>
source | **oneof:** `source_image_id` or `source_snapshot_id`<br>
&nbsp;&nbsp;source_image_id | **string**<br>ID of the image that was used for disk creation. 
&nbsp;&nbsp;source_snapshot_id | **string**<br>ID of the snapshot that was used for disk creation. 
instance_ids[] | **string**<br>Array of instances to which the disk is attached. 
disk_placement_policy | **[DiskPlacementPolicy](#DiskPlacementPolicy1)**<br>Placement policy configuration. 


### DiskPlacementPolicy {#DiskPlacementPolicy1}

Field | Description
--- | ---
placement_group_id | **string**<br>Placement group ID. 


## Create {#Create}

Creates a disk in the specified folder. <br>You can create an empty disk or restore it from a snapshot or an image. Method starts an asynchronous operation that can be cancelled while it is in progress.

**rpc Create ([CreateDiskRequest](#CreateDiskRequest)) returns ([operation.Operation](#Operation))**

Metadata and response of Operation:<br>
	&nbsp;&nbsp;&nbsp;&nbsp;Operation.metadata:[CreateDiskMetadata](#CreateDiskMetadata)<br>
	&nbsp;&nbsp;&nbsp;&nbsp;Operation.response:[Disk](#Disk2)<br>

### CreateDiskRequest {#CreateDiskRequest}

Field | Description
--- | ---
folder_id | **string**<br>Required. ID of the folder to create a disk in. To get the folder ID use a [yandex.cloud.resourcemanager.v1.FolderService.List](/docs/resource-manager/api-ref/grpc/folder_service#List) request. The maximum string length in characters is 50.
name | **string**<br>Name of the disk. Value must match the regular expression ` |[a-z]([-a-z0-9]{0,61}[a-z0-9])? `.
description | **string**<br>Description of the disk. The maximum string length in characters is 256.
labels | **map<string,string>**<br>Resource labels as `key:value` pairs. No more than 64 per resource. The maximum string length in characters for each value is 63. Each value must match the regular expression ` [-_./\\@0-9a-z]* `. The string length in characters for each key must be 1-63. Each key must match the regular expression ` [a-z][-_./\\@0-9a-z]* `.
type_id | **string**<br>ID of the disk type. To get a list of available disk types use the [yandex.cloud.compute.v1.DiskTypeService.List](/docs/compute/api-ref/grpc/disk_type_service#List) request. The maximum string length in characters is 50.
zone_id | **string**<br>Required. ID of the availability zone where the disk resides. To get a list of available zones use the [yandex.cloud.compute.v1.ZoneService.List](/docs/compute/api-ref/grpc/zone_service#List) request. The maximum string length in characters is 50.
size | **int64**<br>Required. Size of the disk, specified in bytes. If the disk was created from a image, this value should be more than the `yandex.cloud.compute.v1.Image.min_disk_size` value. Acceptable values are 4194304 to 28587302322176, inclusive.
source | **oneof:** `image_id` or `snapshot_id`<br>
&nbsp;&nbsp;image_id | **string**<br>ID of the image to create the disk from. The maximum string length in characters is 50.
&nbsp;&nbsp;snapshot_id | **string**<br>ID of the snapshot to restore the disk from. The maximum string length in characters is 50.
block_size | **int64**<br>Block size used for disk, specified in bytes. The default is 4096. 
disk_placement_policy | **[DiskPlacementPolicy](#DiskPlacementPolicy2)**<br>Placement policy configuration. 


### DiskPlacementPolicy {#DiskPlacementPolicy2}

Field | Description
--- | ---
placement_group_id | **string**<br>Placement group ID. 


### Operation {#Operation}

Field | Description
--- | ---
id | **string**<br>ID of the operation. 
description | **string**<br>Description of the operation. 0-256 characters long. 
created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br>Creation timestamp. 
created_by | **string**<br>ID of the user or service account who initiated the operation. 
modified_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br>The time when the Operation resource was last modified. 
done | **bool**<br>If the value is `false`, it means the operation is still in progress. If `true`, the operation is completed, and either `error` or `response` is available. 
metadata | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)<[CreateDiskMetadata](#CreateDiskMetadata)>**<br>Service-specific metadata associated with the operation. It typically contains the ID of the target resource that the operation is performed on. Any method that returns a long-running operation should document the metadata type, if any. 
result | **oneof:** `error` or `response`<br>The operation result. If `done == false` and there was no failure detected, neither `error` nor `response` is set. If `done == false` and there was a failure detected, `error` is set. If `done == true`, exactly one of `error` or `response` is set.
&nbsp;&nbsp;error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**<br>The error result of the operation in case of failure or cancellation. 
&nbsp;&nbsp;response | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)<[Disk](#Disk2)>**<br>if operation finished successfully. 


### CreateDiskMetadata {#CreateDiskMetadata}

Field | Description
--- | ---
disk_id | **string**<br>ID of the disk that is being created. 


### Disk {#Disk2}

Field | Description
--- | ---
id | **string**<br>ID of the disk. 
folder_id | **string**<br>ID of the folder that the disk belongs to. 
created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br> 
name | **string**<br>Name of the disk. 1-63 characters long. 
description | **string**<br>Description of the disk. 0-256 characters long. 
labels | **map<string,string>**<br>Resource labels as `key:value` pairs. Maximum of 64 per resource. 
type_id | **string**<br>ID of the disk type. 
zone_id | **string**<br>ID of the availability zone where the disk resides. 
size | **int64**<br>Size of the disk, specified in bytes. 
block_size | **int64**<br>Block size of the disk, specifiedin bytes. 
product_ids[] | **string**<br>License IDs that indicate which licenses are attached to this resource. License IDs are used to calculate additional charges for the use of the virtual machine. <br>The correct license ID is generated by Yandex.Cloud. IDs are inherited by new resources created from this resource. <br>If you know the license IDs, specify them when you create the image. For example, if you create a disk image using a third-party utility and load it into Yandex Object Storage, the license IDs will be lost. You can specify them in the [yandex.cloud.compute.v1.ImageService.Create](/docs/compute/api-ref/grpc/image_service#Create) request. 
status | enum **Status**<br>Current status of the disk. <ul><li>`CREATING`: Disk is being created.</li><li>`READY`: Disk is ready to use.</li><li>`ERROR`: Disk encountered a problem and cannot operate.</li><li>`DELETING`: Disk is being deleted.</li><ul/>
source | **oneof:** `source_image_id` or `source_snapshot_id`<br>
&nbsp;&nbsp;source_image_id | **string**<br>ID of the image that was used for disk creation. 
&nbsp;&nbsp;source_snapshot_id | **string**<br>ID of the snapshot that was used for disk creation. 
instance_ids[] | **string**<br>Array of instances to which the disk is attached. 
disk_placement_policy | **[DiskPlacementPolicy](#DiskPlacementPolicy3)**<br>Placement policy configuration. 


### DiskPlacementPolicy {#DiskPlacementPolicy3}

Field | Description
--- | ---
placement_group_id | **string**<br>Placement group ID. 


## Update {#Update}

Updates the specified disk.

**rpc Update ([UpdateDiskRequest](#UpdateDiskRequest)) returns ([operation.Operation](#Operation1))**

Metadata and response of Operation:<br>
	&nbsp;&nbsp;&nbsp;&nbsp;Operation.metadata:[UpdateDiskMetadata](#UpdateDiskMetadata)<br>
	&nbsp;&nbsp;&nbsp;&nbsp;Operation.response:[Disk](#Disk3)<br>

### UpdateDiskRequest {#UpdateDiskRequest}

Field | Description
--- | ---
disk_id | **string**<br>Required. ID of the Disk resource to update. To get the disk ID use a [DiskService.List](#List) request. The maximum string length in characters is 50.
update_mask | **[google.protobuf.FieldMask](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/field-mask)**<br>Field mask that specifies which fields of the Disk resource are going to be updated. 
name | **string**<br>Name of the disk. Value must match the regular expression ` |[a-z]([-a-z0-9]{0,61}[a-z0-9])? `.
description | **string**<br>Description of the disk. The maximum string length in characters is 256.
labels | **map<string,string>**<br>Resource labels as `key:value` pairs. <br>Existing set of `labels` is completely replaced by the provided set. No more than 64 per resource. The maximum string length in characters for each value is 63. Each value must match the regular expression ` [-_./\\@0-9a-z]* `. The string length in characters for each key must be 1-63. Each key must match the regular expression ` [a-z][-_./\\@0-9a-z]* `.
size | **int64**<br>Size of the disk, specified in bytes. Acceptable values are 4194304 to 4398046511104, inclusive.
disk_placement_policy | **[DiskPlacementPolicy](#DiskPlacementPolicy4)**<br>Placement policy configuration. 


### DiskPlacementPolicy {#DiskPlacementPolicy4}

Field | Description
--- | ---
placement_group_id | **string**<br>Placement group ID. 


### Operation {#Operation1}

Field | Description
--- | ---
id | **string**<br>ID of the operation. 
description | **string**<br>Description of the operation. 0-256 characters long. 
created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br>Creation timestamp. 
created_by | **string**<br>ID of the user or service account who initiated the operation. 
modified_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br>The time when the Operation resource was last modified. 
done | **bool**<br>If the value is `false`, it means the operation is still in progress. If `true`, the operation is completed, and either `error` or `response` is available. 
metadata | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)<[UpdateDiskMetadata](#UpdateDiskMetadata)>**<br>Service-specific metadata associated with the operation. It typically contains the ID of the target resource that the operation is performed on. Any method that returns a long-running operation should document the metadata type, if any. 
result | **oneof:** `error` or `response`<br>The operation result. If `done == false` and there was no failure detected, neither `error` nor `response` is set. If `done == false` and there was a failure detected, `error` is set. If `done == true`, exactly one of `error` or `response` is set.
&nbsp;&nbsp;error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**<br>The error result of the operation in case of failure or cancellation. 
&nbsp;&nbsp;response | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)<[Disk](#Disk3)>**<br>if operation finished successfully. 


### UpdateDiskMetadata {#UpdateDiskMetadata}

Field | Description
--- | ---
disk_id | **string**<br>ID of the Disk resource that is being updated. 


### Disk {#Disk3}

Field | Description
--- | ---
id | **string**<br>ID of the disk. 
folder_id | **string**<br>ID of the folder that the disk belongs to. 
created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br> 
name | **string**<br>Name of the disk. 1-63 characters long. 
description | **string**<br>Description of the disk. 0-256 characters long. 
labels | **map<string,string>**<br>Resource labels as `key:value` pairs. Maximum of 64 per resource. 
type_id | **string**<br>ID of the disk type. 
zone_id | **string**<br>ID of the availability zone where the disk resides. 
size | **int64**<br>Size of the disk, specified in bytes. 
block_size | **int64**<br>Block size of the disk, specifiedin bytes. 
product_ids[] | **string**<br>License IDs that indicate which licenses are attached to this resource. License IDs are used to calculate additional charges for the use of the virtual machine. <br>The correct license ID is generated by Yandex.Cloud. IDs are inherited by new resources created from this resource. <br>If you know the license IDs, specify them when you create the image. For example, if you create a disk image using a third-party utility and load it into Yandex Object Storage, the license IDs will be lost. You can specify them in the [yandex.cloud.compute.v1.ImageService.Create](/docs/compute/api-ref/grpc/image_service#Create) request. 
status | enum **Status**<br>Current status of the disk. <ul><li>`CREATING`: Disk is being created.</li><li>`READY`: Disk is ready to use.</li><li>`ERROR`: Disk encountered a problem and cannot operate.</li><li>`DELETING`: Disk is being deleted.</li><ul/>
source | **oneof:** `source_image_id` or `source_snapshot_id`<br>
&nbsp;&nbsp;source_image_id | **string**<br>ID of the image that was used for disk creation. 
&nbsp;&nbsp;source_snapshot_id | **string**<br>ID of the snapshot that was used for disk creation. 
instance_ids[] | **string**<br>Array of instances to which the disk is attached. 
disk_placement_policy | **[DiskPlacementPolicy](#DiskPlacementPolicy5)**<br>Placement policy configuration. 


### DiskPlacementPolicy {#DiskPlacementPolicy5}

Field | Description
--- | ---
placement_group_id | **string**<br>Placement group ID. 


## Delete {#Delete}

Deletes the specified disk. <br>Deleting a disk removes its data permanently and is irreversible. However, deleting a disk does not delete any snapshots or images previously made from the disk. You must delete snapshots and images separately. <br>It is not possible to delete a disk that is attached to an instance.

**rpc Delete ([DeleteDiskRequest](#DeleteDiskRequest)) returns ([operation.Operation](#Operation2))**

Metadata and response of Operation:<br>
	&nbsp;&nbsp;&nbsp;&nbsp;Operation.metadata:[DeleteDiskMetadata](#DeleteDiskMetadata)<br>
	&nbsp;&nbsp;&nbsp;&nbsp;Operation.response:[google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty)<br>

### DeleteDiskRequest {#DeleteDiskRequest}

Field | Description
--- | ---
disk_id | **string**<br>Required. ID of the disk to delete. To get the disk ID use a [DiskService.List](#List) request. The maximum string length in characters is 50.


### Operation {#Operation2}

Field | Description
--- | ---
id | **string**<br>ID of the operation. 
description | **string**<br>Description of the operation. 0-256 characters long. 
created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br>Creation timestamp. 
created_by | **string**<br>ID of the user or service account who initiated the operation. 
modified_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br>The time when the Operation resource was last modified. 
done | **bool**<br>If the value is `false`, it means the operation is still in progress. If `true`, the operation is completed, and either `error` or `response` is available. 
metadata | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)<[DeleteDiskMetadata](#DeleteDiskMetadata)>**<br>Service-specific metadata associated with the operation. It typically contains the ID of the target resource that the operation is performed on. Any method that returns a long-running operation should document the metadata type, if any. 
result | **oneof:** `error` or `response`<br>The operation result. If `done == false` and there was no failure detected, neither `error` nor `response` is set. If `done == false` and there was a failure detected, `error` is set. If `done == true`, exactly one of `error` or `response` is set.
&nbsp;&nbsp;error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**<br>The error result of the operation in case of failure or cancellation. 
&nbsp;&nbsp;response | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)<[google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty)>**<br>if operation finished successfully. 


### DeleteDiskMetadata {#DeleteDiskMetadata}

Field | Description
--- | ---
disk_id | **string**<br>ID of the disk that is being deleted. 


## ListOperations {#ListOperations}

Lists operations for the specified disk.

**rpc ListOperations ([ListDiskOperationsRequest](#ListDiskOperationsRequest)) returns ([ListDiskOperationsResponse](#ListDiskOperationsResponse))**

### ListDiskOperationsRequest {#ListDiskOperationsRequest}

Field | Description
--- | ---
disk_id | **string**<br>Required. ID of the Disk resource to list operations for. The maximum string length in characters is 50.
page_size | **int64**<br>The maximum number of results per page to return. If the number of available results is larger than `page_size`, the service returns a [ListDiskOperationsResponse.next_page_token](#ListDiskOperationsResponse) that can be used to get the next page of results in subsequent list requests. The maximum value is 1000.
page_token | **string**<br>Page token. To get the next page of results, set `page_token` to the [ListDiskOperationsResponse.next_page_token](#ListDiskOperationsResponse) returned by a previous list request. The maximum string length in characters is 100.


### ListDiskOperationsResponse {#ListDiskOperationsResponse}

Field | Description
--- | ---
operations[] | **[operation.Operation](#Operation3)**<br>List of operations for the specified disk. 
next_page_token | **string**<br>This token allows you to get the next page of results for list requests. If the number of results is larger than [ListDiskOperationsRequest.page_size](#ListDiskOperationsRequest), use the `next_page_token` as the value for the [ListDiskOperationsRequest.page_token](#ListDiskOperationsRequest) query parameter in the next list request. Each subsequent list request will have its own `next_page_token` to continue paging through the results. 


### Operation {#Operation3}

Field | Description
--- | ---
id | **string**<br>ID of the operation. 
description | **string**<br>Description of the operation. 0-256 characters long. 
created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br>Creation timestamp. 
created_by | **string**<br>ID of the user or service account who initiated the operation. 
modified_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**<br>The time when the Operation resource was last modified. 
done | **bool**<br>If the value is `false`, it means the operation is still in progress. If `true`, the operation is completed, and either `error` or `response` is available. 
metadata | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)**<br>Service-specific metadata associated with the operation. It typically contains the ID of the target resource that the operation is performed on. Any method that returns a long-running operation should document the metadata type, if any. 
result | **oneof:** `error` or `response`<br>The operation result. If `done == false` and there was no failure detected, neither `error` nor `response` is set. If `done == false` and there was a failure detected, `error` is set. If `done == true`, exactly one of `error` or `response` is set.
&nbsp;&nbsp;error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**<br>The error result of the operation in case of failure or cancellation. 
&nbsp;&nbsp;response | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)**<br>The normal response of the operation in case of success. If the original method returns no data on success, such as Delete, the response is [google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty). If the original method is the standard Create/Update, the response should be the target resource of the operation. Any method that returns a long-running operation should document the response type, if any. 

