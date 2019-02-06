This OVF package requires unsupported hardware.
Details: Line 33: Unsupported hardware family 'virtualbox-2.2'.

Now you can convert the OVA in an OVF with the following command:

ovftool.exe --lax source.ova destination.ovf
OR Unzip
This command will create three files: a .MF file, an .OVF file and a .VMDK.

Open the .OVF file in a text editor and change all VirtualBox hardware.

Change this:

<vssd:VirtualSystemType>virtualbox-2.2</vssd:VirtualSystemType>
with:

<vssd:VirtualSystemType>vmx-07</vssd:VirtualSystemType>
Change this:

<Item>
<rasd:Address>0</rasd:Address>
<rasd:Caption>sataController0</rasd:Caption>
<rasd:Description>SATA Controller</rasd:Description>
<rasd:ElementName>sataController0</rasd:ElementName>
<rasd:InstanceID>5</rasd:InstanceID>
<rasd:ResourceSubType>AHCI</rasd:ResourceSubType>
<rasd:ResourceType>20</rasd:ResourceType>
</Item>
with:

<Item>
<rasd:Address>0</rasd:Address>
<rasd:Caption>SCSIController</rasd:Caption>
<rasd:Description>SCSI Controller</rasd:Description>
<rasd:ElementName>SCSIController</rasd:ElementName>
<rasd:InstanceID>5</rasd:InstanceID>
<rasd:ResourceSubType>lsilogic</rasd:ResourceSubType>
<rasd:ResourceType>6</rasd:ResourceType>
</Item>
Save and close. Now your edited file screwed the integrity check. To fix it calculate the SHA1 for the .OVF file (for example using sha1sum or fciv.exe (download), open the .MF file a substitute the present hash with the calculated one.
OR Just renamed the .mf to .mf.old
