# VPC Dynamic Inventory Examples

This directory contains examples for using the IBM Cloud VPC dynamic inventory plugin.

## Floating IPs Example

The `floating-ips.vpc.yml` file demonstrates how to configure the VPC inventory plugin to use floating IP addresses instead of private IP addresses for your virtual server instances.

### Prerequisites

1. Install the IBM Cloud collection:
   ```bash
   ansible-galaxy collection install ibm.cloudcollection
   ```

2. Set your IBM Cloud API key:
   ```bash
   export IC_API_KEY="your-api-key-here"
   ```

### Usage

```bash
# Generate inventory with floating IPs
ansible-inventory -i floating-ips.vpc.yml --list --yaml

# Use in a playbook
ansible-playbook -i floating-ips.vpc.yml your-playbook.yml
```

### Key Features Demonstrated

- **Floating IP Usage**: `use_floating_ips: true` - Uses public floating IPs instead of private IPs
- **Region Selection**: Configure which IBM Cloud regions to query
- **Filtering**: Filter instances by status and other attributes
- **Custom Groups**: Create dynamic groups based on instance properties
- **Host Variables**: Add custom variables to inventory hosts

### Notes

- Only instances with floating IP addresses attached will be included in the inventory when `use_floating_ips: true`
- The inventory file must have a `.vpc.yml` or `.vpc.yaml` extension
- Cache is disabled in this example for testing purposes - remove `cache: false` for production use
