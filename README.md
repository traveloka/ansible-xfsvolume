# ansible-xfsvolume
Ansible role to ensures given device is formated with XFS and mounted at the given mount point.

## Requirements ##

Requires xfsprogs to be installed on the remote system.

## Role Variables ##

### Defaults ###

    - name: xfs_volume_device
      desc: Block device to format and mount
      value: /dev/xvdf

    - name: xfs_volume_mount
      desc: Directory to mount block device to
      value: /data

    - name: xfs_volume_opts
      desc: Mounting options
      value: noatime,noexec,nodiratime

    - name: xfs_volume_state
      desc: Desired state of the volume (mounted|unmounted)
      value: mounted

    - name: xfs_volume_force_format
      desc: Whether to force format device with existing filesystem
      value: no

### Vars ###

These vars are not meant to be overridden, but can be used by others.

    - name: xfs_volume_fstype
      desc: Filesystem to format the device with
      value: xfs

## Dependencies ##

- https://github.com/traveloka/ansible-xfsprogs

## Example Playbook ##

    - hosts: servers
      roles:
         - role: xfs_volume
           xfs_volume_device: /dev/sdb
           xfs_volume_mount: /data
