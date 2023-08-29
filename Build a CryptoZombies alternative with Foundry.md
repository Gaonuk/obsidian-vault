#### Some resources to build  the integrated IDE
- https://codesandbox.io/s/monaco-editor-demo-nextjs-m6n38?file=/pages/index.tsx
- https://www.freecodecamp.org/news/how-to-build-react-based-code-editor/
- https://ahmadrosid.com/blog/codemirror-with-nextjs
- https://www.smashingmagazine.com/2022/01/building-web-code-editor/
- https://codemirror.net/index.html
- https://www.geeksforgeeks.org/build-an-online-code-compiler-using-react-js-and-node-js/
- https://github.com/webtutsplus/code-editor
- https://theia-ide.org/

#### Some inspiration
- https://cryptozombies.io/
- https://nodeguardians.io/
- https://remix.ethereum.org
- https://labs.iximiuz.com/

#### Main guide to follow for stack and tools
- https://iximiuz.com/en/posts/iximiuz-labs-story/
- https://twitter.com/iximiuz/status/1640380028952227843
- https://fly.io/docs/machines/
- https://github.com/yudai/gotty
- https://xtermjs.org/
- https://firecracker-microvm.github.io/
- https://iximiuz.com/en/posts/containers-vs-pods/
- https://github.com/alexellis/firecracker-init-lab
- https://github.com/weaveworks/ignite
- https://jvns.ca/blog/2023/05/25/new-playground--memory-spy/
- https://github.com/alexellis/arkade
### Stack to use
- Typescript (Frontend with NextJS)
- Rust? trpc?
- Shadcn UI
- Two main daemons, both expose HTTP APIs (via [chi](https://github.com/go-chi/chi))
	- systemd service
	- docker container
- Docker:
	- For development purposes - various dev tools are containerized.
	- As a means to package and deploy the daemons, microVM rootfs and kernel images, etc.
	- As a runtime for one of the daemons and surrounding infrastructure (Redis, Nginx, Envoy, etc.).
	- As a runtime for playgrounds - Firecracker microVMs are launched inside Docker containers.

- Nginx - as a reverse-proxy in front of the backend daemons.
- Envoy - as a transparent TCP egress proxy for the microVMs
- Redis - as a storage for daemons' state and as a message broker between them. (can use Dragonfly)

Hosting
- Frontend: Vercel
- Backend: fly.io Machines
- Database: Planetscale
- Workers?: Hetzner Auction


## TODO List

- [ ] Start the repo
- [ ] Add a basic homepage
- [ ] Add a get request in the backend
- [ ] Create an account in the respective services needed to build this system
- [ ] Check out all of the posts for building the online code editor
- [ ] Implement a very basic code editor that handles JS
- [ ] Make that same code editor handle Solidity
- [ ] Check how to install libraries in the vms that will run the code
- [ ] Try installing foundry automatically in the vm for compiling the code
- [ ] Make the first code compile using the vm and the code editor you built
- [ ] Start adding some style and showcase on Twitter for people to see
- [ ] Add a simple logo
- [ ] Build a homepage using Framer and some AI to build it
- [ ] ??
- [ ] Profit? (Pray god Gakonst will sponsor this like wagmi)
