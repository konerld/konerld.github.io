# ESXI CLI


## HOW TO

### How to control esxi with CLI ?

    esxcli

### How to list all volumes ?

    ls -la /vmfs/volumes/

### How to list all VMs ?
Full list:

    esxcli vm process list

Compact list:

    vim-cmd vmsvc/getallvms

### How to list VMs snapshots ?

    vim-cmd vmsvc/snapshot.get {VM_number_from_short_VMs_list}

## How to create VM snapshot ?

    vim-cmd vmsvc/snapshot.create {VM_id_from_short_VM_list} {snaphot_name}

### How to delete snapshot?

    vim-cmd vmsvc/snapshot.remove {VM_id} {snapshot_id}

