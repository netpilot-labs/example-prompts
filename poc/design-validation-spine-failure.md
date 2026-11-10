# SONiC Fabric Design Validation: Prove It Survives a Spine Failure

A team demo in one prompt: build a SONiC leaf-spine fabric, then shut a spine and prove traffic still flows through the other one.

## The Prompt

Open it [prefilled in NetPilot](https://app.netpilot.io/?prompt=Build%20a%20SONiC%20leaf-spine%20fabric%3A%20two%20spines%20in%20AS%2065000%2C%20leaf1%20in%20AS%2065001%20and%20leaf2%20in%20AS%2065002%2C%20eBGP%20on%20%2F31%20point-to-point%20links%2C%20and%20a%20Linux%20host%20on%20each%20leaf%2C%20host1%20at%20192.168.1.10%2F24%20behind%20leaf1%20and%20host2%20at%20192.168.2.10%2F24%20behind%20leaf2.%20Deploy%20it%20and%20show%20each%20leaf%20learning%20the%20other%20LAN%20over%20two%20ECMP%20paths.%20Then%20validate%20the%20design%20against%20a%20spine%20failure%3A%20shut%20down%20spine1%27s%20links%20to%20both%20leaves%2C%20show%20each%20leaf%20now%20reaching%20the%20other%20LAN%20through%20spine2%20only%2C%20and%20ping%20host2%20from%20host1.), or paste it:

> Build a SONiC leaf-spine fabric: two spines in AS 65000, leaf1 in AS 65001 and leaf2 in AS 65002, eBGP on /31 point-to-point links, and a Linux host on each leaf, host1 at 192.168.1.10/24 behind leaf1 and host2 at 192.168.2.10/24 behind leaf2. Deploy it and show each leaf learning the other LAN over two ECMP paths. Then validate the design against a spine failure: shut down spine1's links to both leaves, show each leaf now reaching the other LAN through spine2 only, and ping host2 from host1.

## What You'll Build

- Two SONiC spines in AS 65000, leaf1 in AS 65001, leaf2 in AS 65002, eBGP on /31 links
- A Linux host behind each leaf, 192.168.1.10/24 and 192.168.2.10/24
- A failure drill: spine1's links to both leaves shut while host1 pings host2

## What Came Back

On our run all 8 eBGP sessions were up before the drill, and each leaf reached the other LAN over two ECMP paths. With spine1's links shut, each leaf dropped to one path through spine2 and host1 kept reaching host2. The longest gap in a ping running five times a second was 2.08 s. The agent added BFD with a 1 s hold on its own, and said why: without it the leaves keep sending to the dead spine for much longer.

## Concepts Demonstrated

- Design validation: a failure case proven on real network OSes before the design is built
- ECMP across two spines, and what happens to it when one spine goes away
- BFD as the difference between a two-second and a multi-minute failover
- Agent-built lab, engineer-verified: every result is a show command you can run yourself on the switch

## Vendors Used

- SONiC (`docker-sonic-vs`), preloaded on every lab VM
- Linux hosts

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- Shut a leaf uplink instead of a whole spine and compare the gap
- Remove BFD and measure how long the leaves keep the dead path
- Swap one spine for Nokia SR Linux and run the same drill across two vendors

## Related Resources

- [Run it yourself: the SONiC leaf-spine lab](https://github.com/netpilot-labs/network-labs/tree/main/sonic/bgp-leaf-spine)
- [SONiC leaf-spine with eBGP and ECMP](../data-center/sonic-bgp-leaf-spine-ecmp.md)
- [Customer-matched POC demo lab](customer-matched-demo-lab.md)
- [Bring NetPilot to your team](https://www.netpilot.io/for-teams)
- [RFC 7938: BGP in large-scale data centers](https://www.rfc-editor.org/rfc/rfc7938)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20a%20SONiC%20leaf-spine%20fabric%3A%20two%20spines%20in%20AS%2065000%2C%20leaf1%20in%20AS%2065001%20and%20leaf2%20in%20AS%2065002%2C%20eBGP%20on%20%2F31%20point-to-point%20links%2C%20and%20a%20Linux%20host%20on%20each%20leaf%2C%20host1%20at%20192.168.1.10%2F24%20behind%20leaf1%20and%20host2%20at%20192.168.2.10%2F24%20behind%20leaf2.%20Deploy%20it%20and%20show%20each%20leaf%20learning%20the%20other%20LAN%20over%20two%20ECMP%20paths.%20Then%20validate%20the%20design%20against%20a%20spine%20failure%3A%20shut%20down%20spine1%27s%20links%20to%20both%20leaves%2C%20show%20each%20leaf%20now%20reaching%20the%20other%20LAN%20through%20spine2%20only%2C%20and%20ping%20host2%20from%20host1.)
