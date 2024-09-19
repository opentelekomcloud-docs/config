:original_name: rms_04_0400.html

.. _rms_04_0400:

Storing Resource Snapshots
==========================

Your resource snapshots will be stored into the specified OBS bucket every 24 hours after you enable the resource recorder.

The path of in an OBS bucket where the resource recorder stores your data takes the form of **${bucket_name}/${bucket_prefix}/RMSLogs/${account_id}/Snapshot/${year}/${month}/\*** The fields before each slash in the path indicate different layers of folders, and **\*** indicates the name of a file. You can go to the **Objects** page on the OBS console and find your resource snapshots based on the paths.

The name of a resource snapshot file consists of the account ID, storage file type, ID of the region where the OBS bucket resides, storage time, randomly generated character string, and sequence number of the file. Each snapshot file can contain information of up to 2,000 resources. If you have more than 2,000 resources, there will be more than one files, and the name of each file will contain a sequence number (such as part-1). If you have less than 2,000 resources, there will be no sequence number in the file name. **.json.gz** indicates that the file is stored as a JSON package.

The following shows an example file name: 0926901ef980f2150fbdc001fdd23e80_Snapshot_eu-de_ResourceSnapshot_2024-07-22T221441Z_90decead-b69b-4522-a090-657d8c299d40_part-1.json.gz.

For more details, see `Searching for an Object or Folder <https://docs.otc.t-systems.com/object-storage-service/umn/obs_console_operation_guide/managing_objects/searching_for_an_object_or_folder.html>`__.

For details about example code for storing resource snapshots, see :ref:`Resource Snapshot Storage Model <rms_06_0400>`.
