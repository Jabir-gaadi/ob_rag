https://chatgpt.com/s/t_6aecd08d628c8191a496c2d8fc02ee0d
# Phase 1 — Computer Science & System Fundamentals

باش تبني أساس قوي يوصلّك مع الوقت لمستوى **Senior DevOps Engineer**، هادي مكتبة منظمة كتغطي Phase 1 كاملة ديال الـ Roadmap ديالك، من Linux وOperating Systems حتى Networking وAutomation وWeb Servers.

حيت كتقرا فـ 1337، وعندك معرفة بـ C وPython وLinux Terminal، الهدف هو ما تضيعش الوقت فكتب Programming للمبتدئين إلا كانت فيها شي حاجة مهمة.

المصادر مقسّمة إلى:
- **Main Books:** الكتب اللي تقرا فعلاً.
- **Supporting Resources:** مراجع مجانية وتمارين.
- **Advanced References:** ترجع ليها ملي تحتاج تعمق أكثر.

## 1. Linux Fundamentals & Advanced Linux Administration

### Main Book — How Linux Works, 3rd Edition
![[Pasted image 20261105184931.png|194]]

**Brian Ward — 2021**

أهم كتاب تبدا به دابا. كيغطي Linux Architecture، Kernel، Processes، Boot، `systemd`، Filesystems، Networking وBasic Shell Scripting.

- [الكتاب الرسمي](https://nostarch.com/howlinuxworks3)

### Advanced Reference — UNIX and Linux System Administration Handbook, 5th Edition
![[Pasted image 20261105184956.png|213]]

**Evi Nemeth وآخرون**

من بعد الأساسيات، هاد الكتاب غادي يعمق فهمك فـ Server Administration، Storage، Security، Monitoring، Troubleshooting وAutomation.

- [الكتاب الرسمي](https://www.pearson.com/en-us/subject-catalog/p/unix-and-linux-system-administration-handbook/P200000000513)

### Supporting Resources

- [The Linux Command Line — William Shotts](https://linuxcommand.org/tlcl.php): كتاب مجاني بصيغة PDF، مفيد للمراجعة ديال Terminal وShell.
- [Linux Journey](https://linuxjourney.com/): دروس وتمارين للـ Linux Fundamentals.
- [Linux man-pages](https://man7.org/linux/man-pages/): مرجع تقني لـ Linux System Calls وLibraries وCommands.

**شنو خاصك تتقن:** Filesystem Hierarchy، Permissions، Users & Groups، Processes، Signals، Boot Process، `systemd`، Logging، Storage، LVM، Package Management، SSH، Firewalls وSystem Troubleshooting.

---

## 2. Operating Systems & Computer Architecture

### Main Book — Operating Systems: Three Easy Pieces (OSTEP)
![[Pasted image 20261105185054.png|289]]

**Remzi & Andrea Arpaci-Dusseau — Already Started**

خليك مكمل فيه. كيغطي CPU Virtualization، Scheduling، Memory Virtualization، Concurrency، Synchronization وPersistence.

- [الكتاب مجاني Online](https://pages.cs.wisc.edu/~remzi/OSTEP/)

### Main Book — Computer Systems: A Programmer's Perspective (CS:APP), 3rd Edition
![[Pasted image 20261105185108.png|249]]
**Randal Bryant & David O'Hallaron**

هادا هو المكمل المهم لـ Computer Architecture. غادي تتعلم Data Representation، Assembly، CPU، Cache، Memory Hierarchy، Linking وSystem-Level Programming.

- [الموقع الرسمي](https://csapp.cs.cmu.edu/3e/)

### Supporting Resources

- [CS:APP Labs](https://csapp.cs.cmu.edu/3e/students.html): تطبيقات على Machine-Level Programming وMemory وSystem-Level Concepts.
- [Nand2Tetris](https://www.nand2tetris.org/): مشاريع لبناء Computer من Logic Gates حتى CPU وSoftware؛ اختياري إلا بغيتي تعمق فـ Hardware Architecture.
- [OSTEP Homework & Simulations](https://pages.cs.wisc.edu/~remzi/OSTEP/): تمارين ديال الكتاب اللي كتقراه.

**شنو خاصك تتقن:** Processes، Threads، System Calls، CPU Scheduling، Virtual Memory، Paging، Context Switching، CPU Registers، Assembly، Cache، Memory Hierarchy، I/O وFile Systems.

وبما أنك خدمتي Concurrency وSynchronization، تقدر تستغل Chapters المرتبطة بهم كمراجعة وتعمق، وتعطي وقت أكبر لـ CPU Scheduling وVirtual Memory وPersistence.

---

## 3. Computer Networking — TCP/IP, DNS, HTTP, SSH

### Main Book — Computer Networking: A Top-Down Approach, 9th Edition
![[Pasted image 20261105185124.png|272]]

**James Kurose & Keith Ross — 2025**

أفضل اختيار ليك باش تتعلم Networking من Application Layer حتى Link Layer. كيغطي HTTP، DNS، TCP، UDP، IP، Routing، Congestion Control وNetwork Security.

- [الموقع الرسمي والتمارين](https://gaia.cs.umass.edu/kurose_ross/index.php)

### Advanced Reference — TCP/IP Illustrated, Volume 1, 2nd Edition
![[Pasted image 20261105185138.png|259]]

**Kevin Fall & W. Richard Stevens**

ممتاز للتعمق فـ TCP/IP Protocols وPacket Behavior، خصوصاً ملي تبدا تحلل Network Traffic.

- [الكتاب الرسمي](https://www.pearson.com/en-us/subject-catalog/p/Fall-TCP-IP-Illustrated-Volume-1-The-Protocols-2nd-Edition/P200000000242)

### Supporting Resources

- [Beej's Guide to Networking Concepts](https://beej.us/guide/bgnet0/): كتاب مجاني باش تفهم Networking Fundamentals.
- [Beej's Guide to Network Programming](https://beej.us/guide/bgnet/): مجاني ومناسب ليك حيث كتخدم بـ C، وكيعلمك Sockets Programming.
- [MDN HTTP Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview): باش تفهم HTTP Requests وResponses.
- [Wireshark Documentation](https://www.wireshark.org/docs/): لتحليل Network Packets.

**شنو خاصك تتقن:** OSI/TCP-IP Models، IPv4/IPv6، Subnetting، TCP Handshake، UDP، Ports، DNS Resolution، Routing، NAT، HTTP/1.1–HTTP/3، TLS/HTTPS، SSH وFirewalls.

---

## 4. Bash Scripting & Shell Automation

### Optional Book — Learning the bash Shell, 3rd Edition
![[Pasted image 20261105185157.png|327]]

**Cameron Newham**

كيغطي Variables، Shell Expansion، Functions، Control Flow، Job Control وDebugging. كتاب قديم نسبياً ولكن مازال فيه مفاهيم مهمة.

- [موقع الكتاب](https://www.oreilly.com/library/view/learning-the-bash/0596009658/)

بالنسبة ليك ماشي ضروري تشري كتاب مستقل على Bash، حيث عندك معرفة بـ Programming، وتقدر تعتمد على هاد المصادر المجانية:

### Supporting Resources

- [BashGuide](https://mywiki.wooledge.org/BashGuide): خليه Main Resource ديالك. كيغطي Scripting، Variables، Quoting، Arrays، Control Flow وGood Practices.
- [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/): مرجع رسمي ومتعمق.
- [MIT — The Missing Semester](https://missing.csail.mit.edu/): Shell، Debugging، Git وDevelopment Tools.
- [ShellCheck](https://www.shellcheck.net/): أداة كتكتشف أخطاء شائعة فـ Shell Scripts.

**شنو خاصك تتقن:** Pipes، Redirection، Quoting، Globbing، Parameter Expansion، Exit Codes، Conditions، Loops، Functions، Signals، `trap`، `cron`، Script Debugging وSafe Error Handling.

---

## 5. Python for DevOps & Automation

### Main Book — Python for DevOps
![[Pasted image 20261105185211.png|281]]

**Noah Gift وآخرون — 2019**

مناسب للهدف ديالك. كيغطي Python Automation، Filesystem Operations، CLI Tools، Process Management، Package Management، Testing وMonitoring.

- [موقع الكتاب](https://www.oreilly.com/library/view/python-for-devops/9781492057680/)

**ملاحظة:** الكتاب من 2019، لذلك ركز فـ Phase 1 على Chapters 2–5 و7–8. الأمثلة المرتبطة بإصدارات Cloud وDocker وKubernetes خاصك تتحقق منها فالتوثيق الحديث ملي توصل ليها.

### Supporting Resources

- [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/): كتاب مجاني، استعمل خصوصاً Chapters الخاصة بـ File Automation وRegex وCLI.
- [Python Standard Library](https://docs.python.org/3/library/): المرجع الرسمي.
- [pytest Documentation](https://docs.pytest.org/en/stable/): لتعلم Automated Testing.

**شنو خاصك تتقن:** `os`، `pathlib`، `subprocess`، `argparse`، `logging`، `json`، Regular Expressions، Environment Variables، Virtual Environments، HTTP APIs، Error Handling، Testing وPython Packaging.

---

## 6. Git, GitHub & Version Control

### Main Book (Free) — Pro Git, 2nd Edition
![[Pasted image 20261105185224.png|242]]

**Scott Chacon & Ben Straub**

من Git Basics حتى Git Internals. غادي تفهم Branching، Merging، Rebasing، Remotes، History Management وDistributed Workflows.

- [قرا الكتاب مجاناً](https://git-scm.com/book/en/v2)

### Supporting Resources

- [Learn Git Branching](https://learngitbranching.js.org/): تمارين تفاعلية باش تفهم Branching وRebasing.
- [GitHub Skills](https://skills.github.com/): تعلم Pull Requests وGitHub Workflows بشكل عملي.
- [GitHub Documentation](https://docs.github.com/en/get-started): GitHub Collaboration وRepository Management.

**شنو خاصك تتقن:** Git Object Model، Commits، Branches، Merge، Rebase، Cherry-pick، Reflog، Reset، Revert، Tags، Git Hooks، Pull Requests، Conflict Resolution وRepository Security.

Git خاصو يكون جزء من الخدمة اليومية ديالك، ماشي غير كتاب تقراه وتساليه.

---

## 7. Web Servers & Reverse Proxies — Nginx & Apache

### Practical Book — NGINX Cookbook, 2nd Edition
![[Pasted image 20261105185244.png|254]]

**Derek DeJonghe — 2022**

كيشرح Nginx Configuration، HTTP/TCP Load Balancing، Reverse Proxy، Caching، Traffic Management وSecurity.

- [موقع الكتاب](https://www.oreilly.com/library/view/nginx-cookbook-2nd/9781098126230/)

ماشي ضروري تبدا بكتاب مدفوع هنا، حيث Official Documentation مفيدة بزاف.

### Supporting Resources

- [Nginx Beginner's Guide](https://nginx.org/en/docs/beginners_guide.html): تعلم Basic Configuration وServing Static Files.
- [Nginx Admin Guide](https://docs.nginx.com/nginx/admin-guide/): Reverse Proxy، Load Balancing، Logging وSecurity.
- [Apache HTTP Server Documentation](https://httpd.apache.org/docs/2.4/): مرجع رسمي لـ Apache.
- [Apache Reverse Proxy Guide](https://httpd.apache.org/docs/2.4/en/howto/reverse_proxy.html): تطبيق Reverse Proxy باستعمال Apache.

**شنو خاصك تتقن:** HTTP Servers، Virtual Hosts، Reverse Proxy، Upstreams، Load Balancing، TLS Certificates، HTTPS Termination، Headers، Timeouts، Caching، Access Logs، Error Logs وWeb Server Security.

ركز على Nginx أولاً، ومن بعد تعلم Apache بالقدر اللي يخليك تفهم Configuration وTroubleshooting ديالو.

---

## أهم الكتب اللي غادي تعتمد عليهم فعلياً

باش ما تضيعش وسط هاد الموارد كاملة، هادي هي المجموعة الأساسية ديالك:

| Subject | Main Resource |
|---|---|
| Linux Administration | How Linux Works |
| Operating Systems | OSTEP |
| Computer Architecture | CS:APP |
| Networking | Computer Networking: A Top-Down Approach |
| Bash | BashGuide |
| Python Automation | Python for DevOps |
| Git & GitHub | Pro Git |
| Web Servers | Nginx Official Documentation |

الكتب الأخرى خليهوم **References**، ماشي مطلوب منك تقراهم كاملين من الغلاف للغلاف.

## Notebook Summary — Phase 1 Learning Objectives

> The first phase of a DevOps engineering roadmap focuses on building strong foundations in Linux administration, operating systems, computer architecture, networking, scripting, automation, version control, and web infrastructure. Operating system theory explains resource virtualization, scheduling, memory management, concurrency, and persistence. Linux administration provides practical skills in process management, system services, permissions, storage, networking, and troubleshooting. Bash and Python enable automation of repetitive system operations, while Git supports reliable version control and collaboration. Networking fundamentals explain how systems communicate through protocols such as TCP/IP, DNS, HTTP, TLS, and SSH. Web servers and reverse proxies introduce service deployment, request routing, traffic management, and load balancing. Mastering these areas through practical projects prepares engineers for containers, CI/CD, cloud infrastructure, and production operations.

---

## 8. كيفاش تقرا الكتب بالتوازي؟

هادي هي الخطة المقترحة باش كل Concept تقراه نظرياً تربطو بـ Linux وPractical Work، وباش ما تقراش 7 كتب كبار دفعة وحدة.

| Stage | Operating Systems & Architecture | Linux & Other Resources | Practical Work |
|---|---|---|---|
| **1. Foundations** | OSTEP: Introduction & Processes | How Linux Works: Ch. 1–2، Pro Git: Ch. 1–3 | Linux VM، Commands، Git Repository |
| **2. Process Management** | OSTEP: CPU Scheduling & Context Switching | How Linux Works: Ch. 8، BashGuide Basics | Process Monitoring وBash Scripts |
| **3. Memory & Architecture** | OSTEP: Virtual Memory & Paging، CS:APP: Ch. 2–3 و6 | How Linux Works: Ch. 3–4 | Memory Inspection، Disks، Filesystems |
| **4. Concurrency & Services** | OSTEP: Concurrency & Synchronization | How Linux Works: Ch. 5–7، Python for DevOps: Ch. 2–3 | `systemd` Service وPython CLI Automation |
| **5. Networking** | CS:APP: Ch. 10–11، OSTEP حسب التقدم | Computer Networking: Application، Transport وNetwork Layers؛ How Linux Works: Ch. 9–10 | DNS، TCP، Wireshark، SSH وSocket Server |
| **6. Automation & Persistence** | OSTEP: Filesystems، Storage & Persistence | How Linux Works: Ch. 11–12، Python for DevOps: Ch. 4–5 و8، Pro Git Advanced | Backup Scripts، Logging، Tests وFile Automation |
| **7. Web Infrastructure** | CS:APP: Ch. 7–9 حسب الحاجة | Nginx Docs، NGINX Cookbook، Apache Docs | Deploy Python App behind Nginx with HTTPS |
| **8. Integration & Review** | مراجعة OSTEP وCS:APP | How Linux Works: Ch. 16–17، System Administration Handbook كمراجع | Final Linux Server Project |

**ملاحظة:** الـ Stages مراحل تعلم وليست أسابيع ثابتة. تقدر تزيد أو تنقص فالمدة حسب مشاريع 1337 والتقدم ديالك.

---

## Project نهائي ديال Phase 1

فآخر المرحلة، الهدف هو تبني **Linux Application Server** متكامل، بلا Docker دابا، باش تفهم كيفاش كتخدم Infrastructure مباشرة على Linux.

### Phase 1 Capstone — Linux Production-Style Server

```text
Client
  |
  v
Nginx — HTTPS & Reverse Proxy
  |
  v
Python HTTP API — Managed by systemd
  |
  v
Local Storage + Logs + Backup Automation
```

**الـ Requirements ديال المشروع:**

- [ ] Configure a Linux server and SSH access
- [ ] Create dedicated users, groups and permissions
- [ ] Develop a small Python HTTP API
- [ ] Manage the application using systemd
- [ ] Configure Nginx as a reverse proxy
- [ ] Configure HTTPS using a trusted certificate in an appropriate environment
- [ ] Write Bash/Python scripts for backup and log analysis
- [ ] Use Git and GitHub to track the project
- [ ] Document installation, recovery and troubleshooting

من الأفضل تدير هاد المشروع داخل VM أو Lab Environment. وإذا وصلتي لمرحلة Server متصل بالإنترنت، خاصك تهتم بالـ Firewall وSSH Hardening وUpdates وSecrets Management قبل ما تعرض الخدمات للعموم.

**الترتيب اللي كنفضل ليك دابا:** كمل OSTEP، وقرا معاه How Linux Works، وخلي Git وBash ممارسة يومية. من بعد دخل CS:APP وNetworking، ثم Python Automation وNginx. ما تنتقلش لـ Docker وKubernetes حتى تكون قادر تفهم وتشخص المشاكل الأساسية ديال Linux Server بوحدك.
