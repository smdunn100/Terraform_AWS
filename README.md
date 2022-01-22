# Terraform_AWS
  Terraform is a critical tool for any engineer that has responsibility for cloud infrastructure. Thus I decided
to add it to my toolset. This project was the result of a tutorial on FreeCodeCamp. The most critical part of the project was
to understand the basic steps that must be taken to create the server. Once these were understood it was just a matter of sifting
through the provider documentation on the Terraform site. The basic steps were as follows: First, obtain access keys to the provider.
I have deleted my access keys for security reasons, but most companies will have a specific policy for this field. Second, I had to create the VPC
and determine a cidr block. Third, I needed to create the gateway and pass it the vpc id. Next, I created a route table with ipv4 and ipv6 routes.
Fifth, I created a subnet. It is good practice to create subnets for multiple availability zones. This will ensure that, should a single zone
go down, the application will not go down with it. Step six was to ensure that my newly created subnet would be associated with my route table.
 To do this I simply passed the id of each one to the other. Next I created security groups for each port. This was one of the tougher steps to
understand, but essentially it comes down to this. Two sets of rules, ingress and egress, can be made to allow directional traffic through
certain ports. So when I create the ingress policy for port 443, I am allowing import tcp traffic from that specific port or I can designate a
port range. The next step is to create a network interface for my subnet. Network interfaces essentially allow the network to connect to
the subnet. The last main step was to create an elastic ip and associate it with the network interface. A key piece of this step is to make
the depends_on argument and enter the gateway. This is a requirement for Terraform because the EIP is reliant upon the Gateway. Thus we need to
ensure that the gateway is established before creating the elastic ip. Once this step is performed all that is needed is to create the server
and install the required software. Most of this information is pulled from aws and the steps can vary depending upon the operating system
being used. The main bug I came across was that the depends_on argument requires a list, but this was a quick fix. More than anything, this
project helped me realize that while I still have a lot to learn, I am very capable of learning the tools required to be a capable team member. 
