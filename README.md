# Azure Virtual Network Topology Manager Project

## Objective and Description
In this project, we will be using Microsoft Azure's Virtual Network Manager to build and deploy a Hub and Spoke Network Topology. Traditionally, buidling a network topology requires a lot manual deployment and resources. The Virtual Network Manager provides us with a seemless solution that you can delegate these tasks to. A hub and spoke topology allows for multiple vitual networks to communicate with each other but dont have to be connected to every other network. In this model, you have central command network (Hub) that acts as a traffic cop where all traffic travels from the Spoke virtual networks; into the central network called the Hub. The Spoke virtual networks can speak together or to a on-premises network but can do so only through the central hub network as a medium. All packet traffic must circumnavigate through the Hub then reach its desired destination for connectivity.
### Skills Learned
- Deployed and managed a Hub and Spoke Model virtual network topology with a virtual network manager


  
  ### Tools Used
- Microsoft Azure
- Virtual Networks
- Hub and Spoke Model
- VPN Gateway
  

## Steps
- Step 1: We first must take a look at the Virtual Network Manager for the hub and spoke topology architectual diagram so that we know what resources and services we need.
  
  <img src="https://i.imgur.com/igSJdqP.png" height="80%" width="80%" alt="Azure Virtual Network Hub and Spoke Steps"/>
  
- Step 2: Now we head over to our Azure portal and search for Vitual Network Manager. We click create to deploy the instance and fill in the specifications. We create a new resource group called "hubspokedemo". We also label the instance itself by the same name as well. We will deploy it in the default east US region. The description should be the name of the instance. Next, we pick what scope the what networks this will manage so we choose azure subscription 1. For the feaures options drop down, it has the "connectivity" and "security admin" options. The connectivity option allows us to create a mesh networks or hub and spoke model between networks within this scope. The security admin allows us to create security rules within the scope. So we select both. We review and create it.
  
  <img src="https://i.imgur.com/mhfCpSc.png" height="40%" width="40%" alt="Azure Virtual Network Hub and Spoke Steps"/> <img src="https://i.imgur.com/raKVqsh.png" height="40%" width="40%" alt="Azure Virtual Network Hub and Spoke Steps"/>
- Step 3: In this next step, we will create soome virtual networks; specifically 3. One will act as the hub and the two others will be the spokes. We will name the hub network Vnetwork-A. We will name the spoke networks Vnetwork-B and Vnetwork-C respectivelly. We will put all of the newtworks under the hubspokedemo resource group. We will make sure each of them have there own seperate IP adresses so there are no conflicts between them. And we will also locate them all in Canada with the hub being in central while the other two spokes are in east. This will show that connectivity works despite the regions. We also want to create tags for each network with the name of network location and the value being where they are located which Canada. 
  
  <img src="https://i.imgur.com/rDwnd4M.png" height="20%" width="20%" alt="Azure Virtual Network Hub and Spoke Steps"/>  <img src="https://i.imgur.com/r71FSWO.png" height="20%" width="20%" alt="Azure Virtual Network Hub and Spoke Steps"/> <img src="https://i.imgur.com/0AqY9M2.png" height="20%" width="20%" alt="Azure Virtual Network Hub and Spoke Steps"/> <img src="https://i.imgur.com/Kv4p1Fh.png" height="20%" width="20%" alt="Azure Virtual Network Hub and Spoke Steps"/> 
- Step 4: In this step, we will deploy a VPN Gateway in our Hub network "Vnetwork-A". It will be the connectivity point for a point-to-site or a site-to-site VPN coming into the Vnetwork-A network group.
  
 <img src="https://i.imgur.com/at87HNM.png" height="40%" width="40%" alt="Azure Virtual Network Hub and Spoke Steps"/>  <img src="https://i.imgur.com/afxuzXO.png" height="40%" width="40%" alt="Azure Virtual Network Hub and Spoke Steps"/> 
- Step 5: Under our hubandspoke resource group, we create a network group called "twonetworks" and place Vnetwork-B and Vnetwork-C in it. We will also add the Vnetworks B and C into this new network group manually
  
   <img src="https://i.imgur.com/i44O5y8.png" height="30%" width="30%" alt="Azure Virtual Network Hub and Spoke Steps"/> <img src="https://i.imgur.com/Hn4IUuz.png" height="30%" width="30%" alt="Azure Virtual Network Hub and Spoke Steps"/> <img src="https://i.imgur.com/diGW4Aq.png" height="30%" width="30%" alt="Azure Virtual Network Hub and Spoke Steps"/> 
- Step 6: Switching over to our Network Manager. We make sure to configure the connictivity configuration and call it hubspokemodel. We choose the hub and spoke model option with Vnetwork-A being in the center and the spokes of B and C refering to it. We allow the networks in the twonetworks group, which are the spokes, to communicate to each othe using this model. We will deploy this configuration and assign it to the Central and East Canada region.
  
  <img src="https://i.imgur.com/bcczDud.png" height="30%" width="30%" alt="Azure Virtual Network Hub and Spoke Steps"/> <img src="https://i.imgur.com/YweFkgL.png" height="30%" width="30%" alt="Azure Virtual Network Hub and Spoke Steps"/> <img src="https://i.imgur.com/v6C34qJ.png" height="30%" width="30%" alt="Azure Virtual Network Hub and Spoke Steps"/>

