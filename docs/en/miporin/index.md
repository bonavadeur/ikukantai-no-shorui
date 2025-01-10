# Scheduler and ExtraController: Miporin - みぽりん

[![release](https://img.shields.io/badge/miporin--v1.0-log?style=flat&label=release&color=hotpink)]()
[![LICENSE](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![CloudNet2024](https://img.shields.io/badge/IEEE--CloudNet--2024-log?style=flat&label=publication&color=dodgerblue)](https://cloudnet2024.ieee-cloudnet.org)

[![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white&link=https%3A%2F%2Fkubernetes.io)](https://kubernetes.io/)
[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)]()
[![Knative](https://img.shields.io/badge/knative-log?style=for-the-badge&logo=knative&logoColor=white&labelColor=%230865AD&color=%230865AD)](https://knative.dev/docs/)
[![Go](https://img.shields.io/badge/go-%2300ADD8.svg?style=for-the-badge&logo=go&logoColor=white)](https://go.dev/)
[![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=Prometheus&logoColor=white)](https://prometheus.io/)

`miporin`-chan is the extra-controller of `ikukantai` Fleet, working alongside and independently of Knative's controller.

![miporin](/assets/images/miporin/miporin_wp.png)

To achieve the [goals](https://github.com/bonavadeur/ikukantai?tab=readme-ov-file#1-motivation) posed by the `ikukantai` Fleet, in addition to modifying Knative's source code, we needed a component acts as a controller that exploits the refined code inside Knative. In theory, we can develop additional logic in Knative's controller component. However, that will be more difficult than developing an extra external component for PoC purposes in the Laboratory (yaa, we work in the Laboratory, not Industry).

The name `miporin` is inspired by the character `Nishizumi Miho` from the anime `Girls und Panzer`. Miho is the tank commander, implying `miporin`'s leadership role in the `ikukantai` fleet (remember that Ooarai High School is located in an aircraft carrier, and, `ikukantai` is implied to be that ship). `miporin` is nickname given to Miho by her friends.
