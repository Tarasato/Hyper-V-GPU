ปิดการ์ดจอออนบอร์ด
สร้าง HostDriverStore ใน system32 ของ VM

เอา FileRepository ใน  DriverStore ของ โฮสต์ มาใส่
เอาไฟล์ขึ้นต้น nv ใน system32 ของ โฮสต์ มาใส่ใน HostDriverStore ใน system32 ของ VM

Run Windows PowerShell Administrator

$vm = "VMName"

if (Get-VMGpuPartitionAdapter -VMName $vm -ErrorAction SilentlyContinue) {
        Remove-VMGpuPartitionAdapter -VMName $vm
}

Set-VM -GuestControlledCacheTypes $true -VMName $vm
Set-VM -LowMemoryMappedIoSpace 1Gb -VMName $vm
Set-VM -HighMemoryMappedIoSpace 32Gb -VMName $vm

Add-VMGpuPartitionAdapter -VMName $vm
