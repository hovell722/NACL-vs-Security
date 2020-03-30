# NACL's vs Security Groups

A Security Group is the firewall of an EC2 instance.

A Network Access Control List (NACL) is the firewall of the Subnet.

NACLs are applicable at the subnet level, so any instance in the subnet with an associated NACL will follow rules of NACL.

That’s not the case with security groups, security groups has to be assigned explicitly to the instance. This means any instances within the subnet group gets the rule applied.

If you have many instances, managing the firewalls using Network ACL can be very useful. Otherwise, with Security group, you have to manually assign a security group to the instances.

## Stateful vs Stateless

Security groups are stateful: This means any changes applied to an incoming rule will be automatically applied to the outgoing rule. e.g. If you allow an incoming port 80, the outgoing port 80 will be automatically opened.

Network ACLs are stateless: This means any changes applied to an incoming rule will not be applied to the outgoing rule. e.g. If you allow an incoming port 80, you would also need to apply the rule for outgoing traffic.

## Rules: Allow or Deny

Security group support allow rules only (by default all rules are denied). e.g. You cannot deny a certain IP address from establishing a connection.

NACL support allow and deny rules. By deny rules, you could explicitly deny a certain IP address to establish a connection example: Block IP address 123.201.57.39 from establishing a connection to an EC2 Instance.

## Defense order

Security group first layer of defence, whereas NACL is second layer of the defence.
