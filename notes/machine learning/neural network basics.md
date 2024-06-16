Deep learning and neural networks, tends to attract more interest than many of the other topics. One of the reasons for the interest is the hope to understand our own mind, which emerges from neural processing in our brain. Another reason is the advances in ML achieved within the recent years by combining massive data sets and deep learning techniques.

## What are neural networks?

To better understand the whole, we will start by discussing the individual units that make it up. A neural network can mean either a "real" biological neural network such as the one in your brain, or an artificial neural networks simulated in a computer.

> Deep learning
> 
> Deep learning refers to certain kinds of machine learning techniques where several "layers" of simple processing units are connected in a network so that the input to the system is passed through each one of them in turn. This architecture has been inspired by the processing of visual information in the brain coming through the eyes and captured by the retina. This depth allows the network to learn more complex structures without requiring unrealistically large amounts of data.
> 
> Neurons, cell bodies, and signals
> 
> A neural network, either biological and artificial, consists of a large number of simple units, neurons, that receive and transmit signals to each other. The neurons are very simple processors of information, consisting of a cell body and wires that connect the neurons to each other. Most of the time, they do nothing but sit still and watch for signals coming in through the wires.
> 
> Dendrites, axons, and synapses
> 
> In the biological lingo, we call the wires that provide the input to the neurons dendrites. Sometimes, depending on the incoming signals, the neuron may fire and send a signal out for the other neurons to receive. The wire that transmits the outgoing signal is called an axon. Each axon may be connected to one or more dendrites at intersections that are called synapses. 

Isolated form its fellow-neurons, a single neuron is quite unimpressive, and capable of only a very restricted set of behaviors. When connected to each other, however, the system resulting from their concerted action can become extremely complex. To find evidence for this, look no further than (to use legal jargon) "Exhibit A": your brain! The behavior of the system is determined by the ways in which the neurons are wired together. Each neuron reacts to the incoming signals in a specific way that can also adapt over time. This adaptation is known to be the key to functions such as memory and learning.

![[notes/machine learning/neuron.png]]
## Why develop artificial neural networks?

The purpose of building artificial models of the brain can be neuroscience, the study of the brain and the nervous system in general. It is tempting to think that by mapping the human brain in enough detail, we can discover the secrets of human and animal cognition and consciousness.

> Modeling the brain
> 
> [The BRAIN initiative](https://www.braininitiative.nih.gov/) led by American neuroscience researchers is pushing forward technologies for imaging, modeling and simulating the brain at a finder and larger scale than before. Some brain research projects are very ambitious in terms of objectives. [The Human Brain](https://www.youtube.com/watch?v=JqMpGrM5ECo) promised in 2012 that "the mysteries of the mind can be solved - soon". After years of work, the Human Brain Project was facing questions about when the [billion euros invested by the European Union](https://www.scientificamerican.com/article/why-the-human-brain-project-went-wrong-and-how-to-fix-it/) will deliver what was promised, even though, to be fair, some less ambitious milestones have been achieved.

However, even while we seem to be almost as far from understanding the mind and consciousness, there are clear milestones that have been achieved in neuroscience. By better understanding of the structure and function of the brain, we are already reaping some concrete rewards. We can, for instance, identify abnormal functioning and try to help the brain avoid them and reinstate normal operation. This can lead to life changing new medical treatments for people suffering from neurological disorders: epilepsy, Alzheimer's disease, problems caused by developmental disorders or damage caused by injuries and so on.

> Looking to the future: brain computer interfaces
> 
> One research direction in neuroscience is brain-computer interfaces that allow interacting with a computer by simply thinking. The current interfaces are very limited and they can be used, for example, to [reconstruct on a very rough level what a person is seeing](https://www.youtube.com/watch?v=Ecvv-EvOj8M), or to [control robotic arms by thought](https://www.youtube.com/watch?v=6QcY7v9Kio4). Perhaps some day we can actually implement [a thought reading machine](https://www.euronews.com/next/2023/05/02/reading-your-mind-this-ai-system-can-translate-thoughts-to-text) that allows precise instructions but currently they belong to science fiction. It is also conceivable that we could feed information into the brain by stimulating it by small electrical pulses. Such stimulation is currently used for therapeutic purposes. Feeding detailed information such as specific words, ideas, memories, or emotions is at least currently science fiction rather than reality, but obviously we know neither the limits of such technology, nor how hard it is to reach them.

We've drifted a little astray from the topic of the note. In fact, another main reason for building artificial neural networks has little to do with understanding biological systems. It is to use biological systems as an inspiration to build better AI and machine learning techniques. The idea is very natural: the brain is amazingly complex information processing system capable of a wide range of intelligent behavior (plus occasionally some not-so-intelligent ones), and therefore, it makes sense to look for inspiration in it when we try to create artificially intelligent systems.

Neural networks have been a major trend in AI since the 1960s. We'll return to the waves of popularity in the history of AI in the final part. Currently neural networks are again at the very top of the list as deep learning is used to achieve significant improvements in many areas such as natural language and image processing, which have traditionally been sore points of AI.

## What is so special about neural networks?

The case for neural networks in general as an approach to AI is based on a similar argument as that for logic-based approaches. In the latter case, it was thought that in order to achieve human-level intelligence, we need to simulate higher-level thought processes, and in particular, manipulation of symbols representing certain concrete or abstract concepts using logical rules.

The argument for neural networks is that by simulating the lower-level, "subsymbolic" data processing on the level of neurons and neural networks, intelligence will emerge. This all sounds very reasonable but keep in mind that in order to build flying machines, we don't build airplanes that flap their wings, or that are made of bones, muscle and feather. Likewise, in artificial neural network, the internal mechanism of the neurons is usually ignored and the artificial neurons are often much simpler than their natural counterparts. The electro-chemical signaling mechanisms between natural neurons are also mostly ignored in artificial models when the goal is to build AI systems rather than simulate biological systems.

Compared to how computers traditionally work, neural networks have certain special features:

#### Neural network key feature 1
For once, in a traditional computer, information is processed in a central processor (aptly named the central processing unit, or CPU for short) which can only focus on doing one thing at a time. The CPU can retrieve data to be processed from the computer's memory, and store the result in the memory. Thus, data storage and processing are handled by two separate components of the computer: the memory and the CPU. In neural networks, the system consists of a large number of neurons, each of which can process information on its own so that instead of having a CPU process each piece of information one after the other, the neurons process vast amounts of information simultaneously.
#### Neural network key feature 2
The second difference is that data storage (memory) and processing isn't separated like in traditional computers. The neurons both store and process information so that there is no need to retrieve data from the memory for processing. The data can be stored short term in the neurons themselves (they either fire or not at any given time) or for longer term storage, in the connections between the neurons - their so called weights, which we will discuss below.

Because of these two differences, neural networks and traditional computers are suited for somewhat different tasks. Even though it is entirely possible to simulate neural networks in traditional computers, which was the way they were used for a long time, their maximum capacity is achieved only when we use special hardware (computer devices) that can process many pieces of information at the same time. This is called **parallel processing**. Incidentally, graphics processors (or graphics processing units, GPUs) have this capability and they have become a const-effective solution for running massive deep learning methods.