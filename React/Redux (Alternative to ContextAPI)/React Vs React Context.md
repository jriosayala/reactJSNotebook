### React Context has some potential disadvantages
- **Deeply Nested Providers**
	 ![[DeeplyNestedProviders.png| 350]]
- **High-Frequency Changes (Performance)**
	React Context is not optimized for high-frequency state changes
	
	> My personal summary is that new context is ready to be used for low frequency unlikely updates (like locale/theme). It's also good to use it in the same way as old context was used. I.e. for static values and then propagate updates through subscriptions. It's not ready to be used as a replacement for all Flux-like state propagation.
	
	\- [Sebastian Markbåge](https://github.com/sebmarkbage)