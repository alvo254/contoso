# Introduction

Completed100 XP

-   1 minute

Sustainable Software Engineering is an emerging discipline at the intersection of climate science, software, hardware, electricity markets, and data-center design. The principles and philosophies of Sustainable Software Engineering are a core set of competencies that are necessary to define, build, and run sustainable software applications. By synthesizing this knowledge, a Sustainable Software Engineer (SSE) can make decisions that have a meaningful impact on the carbon pollution of their applications.

## Learning objectives

By the end of this module, you'll be able to:

-   Identify the eight principles of Sustainable Software Engineering.
-   Understand the two philosophies of Sustainable Software Engineering.

## Prerequisites

-   Familiarity with general computing concepts


# Overview of Sustainable Software Engineering

Completed100 XP

-   3 minutes

## Eight principles of Sustainable Software Engineering

There are eight principles of Sustainable Software Engineering that form a shared understanding of what it means to be a Sustainable Software Engineer. The subsequent units in this module will provide a basic introduction to each of these principles.

1.  **Carbon**: Build applications that are carbon efficient.
    
2.  **Electricity**: Build applications that are energy-efficient.
    
3.  **Carbon Intensity**: Consume electricity with the lowest carbon intensity.
    
4.  **Embodied Carbon**: Build applications that are hardware efficient.
    
5.  **Energy Proportionality**: Maximize the energy efficiency of hardware.
    
6.  **Networking**: Reduce the amount of data and distance it must travel across the network.
    
7.  **Demand Shaping**: Build carbon-aware applications.
    
8.  **Optimization**: Focus on step-by-step optimizations that increase the overall carbon efficiency.
    

These eight principles are independent of:

-   Application domain.
-   Organization size or type.
-   Cloud vendor or self-hosted.
-   Programming language or framework.

## Two philosophies of Sustainable Software Engineering

Alongside the eight principles of Sustainable Software Engineering, there are two philosophies.

1.  **Everyone has a part to play in the climate solution**
    
    If you're reading this document and identify as Green, know you're part of a massive global movement of people who care and are taking action. Greens work in every discipline across engineering, from designing silicon to designing user experiences.
    
    Nothing happens in isolation, everything is connected, and small changes lead to significant changes. Even the act of normalizing a discussion about sustainability in technical meetings will empower others to raise their voices. That's how you create change in any organization.
    
    As Sustainable Software Engineers, we believe that everyone has a part to play in the climate solution. Sustainable Software Engineering is inclusive. Whatever sector, industry, role, technology; there's always something you can do to have an impact.
    
2.  **Sustainability is enough, all by itself, to justify our work**
    
    As Sustainable Software Engineers, we recognize there are many advantages to building sustainable applications. They're almost always cheaper, they're often more performant, and they're often more resilient. But the primary reason we are practicing Sustainable Software Engineering is for sustainability; everything else is an added advantage.


# Principle 1: Carbon

Completed100 XP

-   2 minutes

Being _green_ means different things to different people, and that's a challenge when it comes to communication and deciding for what to optimize. For Sustainable Software Engineering, our focus is carbon, and that's why the first principle of Sustainable Software Engineering is to build applications that are carbon efficient.

## What's carbon?

Greenhouse gases (GHG) act as a blanket that increases the Earth's temperature, which is a natural phenomenon. However, due to human activities, the global climate is changing much faster than animals and plants can adapt. How human society will adapt is still an open question.

There are many different GHGs. The most common GHG emitted through human activity is carbon dioxide (CO2). To make calculations more manageable, we normalize all GHG numbers to _carbon dioxide equivalent_ (CO2eq). For example, one ton of methane has the same warming effect as about 25 tons of CO2, so we normalize it to 25 tons CO2eq. We may shorten even further to just **carbon**, which is often used to refer to all GHGs.

## Net-zero carbon targets

The goal set by the [UN IPCC](https://www.theguardian.com/environment/2011/dec/06/what-is-ipcc) and agreed and ratified by 195 states in the [Paris Climate Agreement](https://unfccc.int/process-and-meetings/the-paris-agreement/the-paris-agreement) is to reduce carbon pollution so that the temperature increase stabilizes to a 1.5°C increase by 2100 when compared to pre-industrial levels.

The temperature increase on the Earth is dependent on the total amount of carbon we have in the atmosphere, not the rate at which we are emitting. To completely halt the rate of temperature increase, we need to stop adding carbon to the atmosphere or achieve net-zero emissions.

Net-zero means for each gram of carbon we emit we also extract one gram, so the overall mass of carbon in the atmosphere remains fixed.

To achieve this, we need to start immediately reducing our carbon emissions to a 45% reduction by 2030 and reach net-zero by 2050.

## Don't waste carbon

We'll always emit carbon through our activities; our goal is that for each gram of carbon we emit into the atmosphere, we make sure we extract the most value from it as possible.

To be _carbon-efficient_ is to minimize the amount of carbon emitted per unit of work.

In the engineering space, the part we play in the climate solution is building applications that are carbon-efficient. Being carbon-efficient is about building applications that add the same value for you or your users, but emit less carbon.


# Principle 2: Electricity

Completed100 XP

-   2 minutes

## Electricity and carbon

Most people think electricity is clean. When we plug something into a wall, our hands don't become dirty, and our laptops don't need exhaust pipes. However, the truth is that most electricity is produced through burning fossil fuel ([usually coal](https://ourworldindata.org/grapher/world-electricity-by-source)) and energy supply is the [single most significant](https://www.eea.europa.eu/data-and-maps/daviz/change-of-co2-eq-emissions-2#tab-chart_4) cause of carbon emission.

Because we can draw a direct line from electricity to carbon emissions, we can consider electricity one of the proxies for carbon.

From the applications running on your smartphone to training machine-learning models running in data centers, all software consumes electricity in its execution. One of the best ways to reduce electricity consumption and the subsequent emissions of carbon pollution made by our software is to make our applications more energy-efficient.

This is why the second principle of Sustainable Software Engineering is to **build applications that are energy-efficient**.

As sustainable engineers, we need to understand electricity. Our journey doesn't start from the computer, it starts from how the electricity that powers our computers is made.

## Energy vs. power

Energy is a measure of an amount of electricity used; the standard unit for Energy is Joules or J. However, another common way of referring to energy consumption is in Kilowatt-hours, or kWh.

Electricity is often reported as either Power or Energy, which are two different concepts:

Energy = Power ✕ Time

-   Energy is the total amount of electricity used, the standard unit for Energy is Joules or J.
    
-   Power is the rate of electricity consumed per unit time; the standard unit of Power is Watt or W. A single Watt is one Joule per second.
    

A common way of referring to energy consumption is _Power over a unit of Time, such as Watt-seconds or Kilowatt-hours_. For example:

-   20 Watt-seconds or 20 Ws is the amount of energy you would get if 20 W were run for one second. Since one Watt is one Joule per second, this value is 20 Joules.
    
-   20 Kilowatt-hours or 20 kWh is the amount of energy you would get if 20,000 Watts were running for one hour.
    
    Energy = 60 ✕ 60 ✕ 20,000 = 72,000,000 Joules = 72 Megajoules (72 MJ)


# Principle 3: Carbon intensity

Completed100 XP

-   6 minutes

The carbon intensity of electricity is a measure of how many carbon (CO2eq) emissions are produced per kilowatt-hour of electricity consumed.

The standard unit of carbon intensity is **gCO2eq/kWh**, or grams of carbon per kilowatt-hour.

Not all electricity is produced in the same way. In different locations and at different times, electricity is made using various sources with varying emissions of carbon. Some sources, such as wind, solar, or hydroelectric, are clean, renewable sources that emit no carbon. Other fossil fuel sources emit varying amounts of carbon to produce electricity. For example, gas-burning power plants emit less carbon than coal-burning power plants.

If your computer was plugged directly into a hydroelectric plant, then the electricity it consumed would have a carbon intensity of **zero gCO2eq/kWh**. A hydroelectric plant emits no carbon to produce that electricity. Most people can't plug directly into hydroelectric plants. Instead, they plug into power grids supplied with electricity from a mix of sources that produce varying amounts of carbon. Therefore, when plugged into a grid, your carbon intensity is usually a number greater than zero.

## Variability of carbon intensity

Carbon intensity changes by location since some regions have an energy mix containing more clean energy sources than other regions.

Carbon intensity also changes over time due to the variable nature of renewable energy. For example, when it's cloudy or the wind isn't blowing, carbon intensity increases because more of the electricity in your mix comes from sources that emit carbon.

![Illustration showing carbon intensity in renewable energy versus fossil fuels.](https://learn.microsoft.com/en-us/training/modules/sustainable-software-engineering-overview/media/5-carbon-intensity-1.svg)

Electricity demand varies during the day, and supply needs to meet that demand. Some of that supply can easily control the power it produces; for example, a coal power plant can burn less coal. Some of that supply can't easily control the power it produces; for example, a wind farm can't control how much the wind blows, it can only throw away (curtail) electricity that was made essentially for free.

![Illustration showing reduced energy demands.](https://learn.microsoft.com/en-us/training/modules/sustainable-software-engineering-overview/media/5-carbon-intensity-2.svg)

As a byproduct of the way energy markets work, as demand for electricity goes down, ordinarily the high emitting fossil fuel sources of power are scaled back first, with renewables scaled back last.

Reducing the amount of electricity consumed in your applications can decrease the carbon intensity of the local grid's energy mix.

## Marginal carbon intensity

If you choose to consume more energy, that energy comes from the marginal power plant. That power plant is one that can control the energy it outputs. Renewables cannot control the sun or the wind, so marginal power plants are often powered by fossil fuels.

The marginal plant emits carbon, and at any moment we have the carbon intensity of the energy mix in the grid, but also the carbon intensity of the energy that would have to be brought online to meet new demand. That's called the marginal carbon intensity.

Fossil-fueled power plants rarely scale down to zero; they have a minimum functioning threshold. Some don't scale at all, and they are considered consistent always-on base load. Because of this, we can sometimes reach the perverse scenario where we throw away (curtail) renewable energy that was created for free to consume energy from fossil-fuel power plants made with a fuel that costs money.

![Illustration showing free renewable engergy.](https://learn.microsoft.com/en-us/training/modules/sustainable-software-engineering-overview/media/5-carbon-intensity-3.svg)

If a new load would be met with supply from a renewable source that would otherwise have been curtailed, then marginal carbon intensity will be **zero gCO2eq/kWh**.

There are moments when the marginal carbon intensity of electricity is **zero gCO2eq/kWh**. Running compute during these times results in **no carbon being emitted** from electricity consumption.

## Demand shifting

There is currently little in the way of storage or buffering in electrical grid systems. Typically electricity is produced so supply always meets demand. If more energy is generated from renewables than is needed to support demand and all our storage options are full, we curtail (throw away) that clean energy. One solution is to shift workloads to times and locations where there is more supply of renewable energy; this is called demand shifting.

If you can be flexible with when and where you run workloads, you can then choose to consume electricity when the carbon intensity is less and pause when carbon intensity is high. For example, training a machine learning model at a different time or in a region where the carbon intensity is much lower.

Studies such as _[Putting a CO2 figure on a piece of computation](https://ieeexplore.ieee.org/document/6128960)_ have shown that these actions can result in a carbon reduction of as much as 45% to 99%, depending on the number of renewables powering the grid.

Look at your application end to end, identify opportunities for being flexible regarding workloads, and use the carbon intensity of electricity to signal when or if to run those workloads.

![Illustration showing carbon intensity over time.](https://learn.microsoft.com/en-us/training/modules/sustainable-software-engineering-overview/media/5-carbon-intensity-4.svg)

## Calculating carbon intensity

Several services allow you to obtain real-time data regarding the current carbon intensity of different electricity grids. Some provide estimates of future carbon intensity, and some give the marginal carbon intensity.

-   [Carbon Intensity API](https://carbonintensity.org.uk/): Free resource for carbon intensity data in the UK.
    
-   [ElectricityMap](https://api.electricitymap.org/): Free for non-commercial single country/region use, premium solutions for commercial and multi-country/region access.
    
-   [WattTime](https://www.watttime.org/): Free for a single grid region, premium solutions for multi-grid, and real-time marginal emissions.


# Principle 4: Embodied carbon

Completed100 XP

-   3 minutes

The device on which you're reading this document released some carbon in its creation; once it reaches the end of life, disposing of it may release more. Embodied carbon (otherwise referred to as "Embedded Carbon") is the amount of carbon pollution emitted during the creation and disposal of a device. When calculating the total carbon pollution for the computers running your software, account for both the carbon pollution to run the computer and the computer's embodied carbon.

## Embodied carbon is significant

Depending on your energy mix's carbon intensity, the embodied carbon cost of a device can be high compared to the carbon cost of the electricity powering it.

For example, a [2019 R640 Dell Server](https://i.dell.com/sites/csdocuments/CorpComm_Docs/en/carbon-footprint-poweredge-r640.pdf) has an amortized embedded carbon cost of 320 kg CO2eq/year. It's also expected to consume 1760.3 kWh/year of electricity. The average carbon intensity in the EU was 0.276 kg CO2eq/kWh for 2019.

Therefore, the total carbon cost will be 320 + (0.276 * 1760.3) = 805 kg of carbon/year, of which 320 kilograms or about 40% is from the embodied carbon. Embodied carbon is a significant contributor to the total emitted carbon of servers.

 Note

The embodied carbon cost is often much higher for consumer devices, sometimes more significant than the lifetime carbon cost from electricity consumption. For an example, reference _[Smartphones Are Killing The Planet Faster Than Anyone Expected](https://www.fastcompany.com/90165365/smartphones-are-wrecking-the-planet-faster-than-anyone-expected)_.

## Don't waste hardware

By the time you buy a computer, it's already emitted a whole load of carbon. Computers also have an expiry date; they get old, can't handle modern workloads, and need to be refreshed. If you think about it in this way, hardware is then a proxy for carbon, so as Sustainable Software Engineers we must be hardware efficient if our goal is to be **carbon-efficient**.

You can do many things to be hardware efficient, but one thing you can do is help extend the expiry date on hardware. Computers don't wear out, there are no moving parts; they just become obsolete. They become obsolete because we are continually creating software that pushes limits.

## Extending the lifespan of hardware

A way to account for embodied carbon is to amortize the carbon over a device's expected life span. For example, if it took 4,000 Kg of carbon to build a hypothetical server and we hoped that the server would have a four-year lifespan, we can consider this equivalent to 1,000 Kg of carbon released per year during its lifespan.

![Diagram of embodied carbon of a server amortized over 4 years.](https://learn.microsoft.com/en-us/training/modules/sustainable-software-engineering-overview/media/6-embodied-carbon-1.svg)

By thinking of embodied carbon in this way, any device, even one that isn't consuming electricity, is effectively releasing carbon over its lifetime. With that in mind, if we were to amortize the same 4,000 Kg of carbon for our hypothetical server over a five-year lifespan instead of four, the carbon released per year would be reduced to 800 Kg.

![Diagram of embodied carbon of the same server amortized over 5 years.](https://learn.microsoft.com/en-us/training/modules/sustainable-software-engineering-overview/media/6-embodied-carbon-2.svg)

If we apply this concept to the lifespan of the 2019 R640 Dell Server that we discussed earlier, the amortized carbon would drop from **320 kg CO2eq/year** to **256 kg CO2eq/year** if we extended its lifespan over five years instead of four.

Hardware is retired either because it breaks down or because it struggles to handle modern workloads. Software can't help with the first; however, if we focus on building applications that can run on older hardware, we can help with the second.


# Principle 5: Energy proportionality


Utilization is a measure of how much of a computer's resources are being used, which is usually represented as a percentage. An idle computer has a low utilization percentage and isn't being utilized, a computer running at its maximum capacity has a high percentage and is being fully utilized.

[Energy proportionality](https://en.wikipedia.org/wiki/Energy_proportional_computing) is a measure of the relationship between power consumed in a computer system and the rate at which useful work is done (its utilization). If the overall power consumption is proportional to the computer's utilization, then it's said to be energy proportional.

In an energy proportional system, the energy efficiency is a constant; no matter the utilization, the energy efficiency remains the same. However, the energy efficiency of hardware is not constant. It varies based on context. Due to the complex interactions of many different components of a hardware device, it can be nonlinear, which means that the relationship between power and utilization is not proportional.

![Diagram showing power versus utilization.](https://learn.microsoft.com/en-us/training/modules/sustainable-software-engineering-overview/media/7-energy-proportionality-1.svg)

At 0% utilization, the computer still draws 100 W; at 50% utilization, it draws 180 W, and at 100% utilization, it draws 200 W. The relationship between power consumption and utilization is not linear, and it doesn't cross the origin.

Because of this relationship, **the more you utilize a computer, the more efficient it becomes at converting electricity to useful computing operations**. Running your work on as few servers as possible with the highest utilization rate maximizes their energy efficiency.

## Static power draw

There are various reasons for this lack of energy proportionality, and one of them is static power draw.

An idle computer, even one at zero percent utilization, still draws electricity. This static power draw varies by configuration and hardware components, but all components have some static power draw. This potential power draw is one of the reasons that PCs, laptops, and mobile devices have power-save modes available. If the device is idle, it will eventually trigger a hibernation mode and put the disk and screen to sleep or even change the CPU frequency. These power-save modes save on electricity, but they have other trade-offs, such as a slower restart when the device wakes up.

Servers are usually not configured for aggressive or even minimal power-saving. Many server use-cases demand full capacity as quickly as possible in response to rapidly changing demands. This scenario can leave many servers in idle modes during low demand periods. An idle server has a cost both from embedded carbon and its inefficient utilization.

### Clock speed

Clock speed (frequency) is the operating speed of a computer or its microprocessor, expressed in cycles per second (megahertz). Dynamically adjusting the clock speed of computing devices is often used in consumer devices to achieve more energy proportionality.

Clock speed denotes how fast a computer can execute instructions.

The energy efficiency of microprocessors changes with clock speed; high clock speeds are often **less** energy-efficient than low clock speeds. For example, in the I7-3770K system, you can run at 3.5 GHz for 50 W, or about 5 GHz for 175 W. An approximate 40% increase in clock speed requires >3✕ power increase.

Taking this information into consideration, reducing the clock speed at times of low utilization can increase energy efficiency, thereby maximizing the energy efficiency of hardware.


# Principle 6: Network efficiency

Completed100 XP

-   2 minutes

A network is a series of switches, routers, and servers. All of the equipment in a network consumes electricity and have embedded carbon. The internet is a global network of devices typically run off the standard local grid energy mix or powered by renewables.

When you send data across the internet, you send that data through many devices in the network, and each of those devices consumes electricity. As a result, any data you send or receive over the internet emits carbon.

![Diagram of nodes in a network run on different energy mixes.](https://learn.microsoft.com/en-us/training/modules/sustainable-software-engineering-overview/media/8-network-efficiency-1.svg)

The amount of carbon emitted to send data depends on many factors:

-   The size of the data
    
-   Distance the data travels
    
-   The number of hops between network devices
    
-   The energy efficiency of the network devices
    
-   The carbon intensity of energy in the region of each device at the time the data is transmitted
    
-   The network protocol used to coordinate data transmission; for example, multiplex, header compression, TLS/Quic
    

We assume the two most important are size and distance, so carbon-efficient applications focus on reducing the amount of data and distance it travels.

A 2019 study by The Shift Project proposed a 1-byte model for estimating the energy used in the transmission of data. To estimate the kWh, multiply the total megabytes of your traffic by 0.0023.

To convert to carbon, we use the average global carbon intensity of 519 gCO2eq/kWh, multiply with 0.519 to get kilograms of carbon. Using this model, we estimate transmitting 1 GB would result in 1024 ✕ 0.0023 ✕ 0.519 = 1.22 kilos of carbon emitted.

The same study also suggested the energy consumed is almost double for data transmitted over mobile networks.

# Principle 7: Demand shaping

Completed100 XP

-   3 minutes

[Demand shifting](https://principles.green/principles/carbon-intensity/#heading-demand-shifting) is the strategy of moving compute to regions or times when the carbon intensity is less; or to put it another way, when the supply of renewable electricity is high.

Demand shaping is a similar strategy, but instead of moving demand to a different region or time, we shape our demand to match the existing supply.

![Diagram of resource supply and demands over time.](https://learn.microsoft.com/en-us/training/modules/sustainable-software-engineering-overview/media/9-demand-shaping-1.svg)

If the supply of renewable energy is high, increase the demand (do more in your applications); if the supply is low, decrease demand (do less in your applications).

-   A great example of this is video-conferencing software. Rather than streaming at the highest quality possible at all times, they often shape the demand by reducing the video quality to prioritize audio.
    
-   Another example is TCP/IP. The transfer speed ramps up in response to how much data can broadcast over the wire.
    
-   A third example is progressive enhancement with the web. The web experience improves depending on the resources and bandwidth available on the end user's device.
    

## Carbon-aware vs. carbon-efficient

Carbon efficiency can be transparent to the end user. You can be more efficient at every level in converting carbon to useful functionality, while still keeping the user experience the same.

But at some point, being transparently more carbon-efficient isn't enough. If the carbon cost of running an application right now is too high, we can change the user experience to reduce carbon emissions further. At the point the user is aware the application is running differently, it becomes a carbon-aware application.

Demand shaping carbon-aware applications is all about the supply of carbon. When the carbon cost of running your application becomes high, shape the demand to match the supply of carbon. This can happen automatically, or the user can make a choice.

## Eco-modes

Eco-modes are often used in life; for instance, in cars or washing machines. When switched on, the performance changes as they consume fewer resources (gas/electricity) to perform the same task. It's not cost-free (otherwise, we would always choose eco-modes), so we make trade-offs. Because it's a trade-off, eco-modes are almost always presented to a user as a choice, and the user decides if they want to go with it and accept the compromises.

Software applications can also have eco-modes, which when engaged change application behavior in potentially two ways:

-   **Intelligence**: Giving users information so they can make informed decisions.
    
-   **Automatic**: The application automatically makes more aggressive decisions to reduce carbon emissions.
    

## Summary

Demand shaping is related to a broader concept in sustainability, which is to reduce consumption. We can achieve a lot by becoming more efficient with resources, but at some point, we also just need to consume less. As Sustainable Software Engineers, to be carbon-efficient means perhaps when the carbon intensity is high, instead of demand-shifting compute, we consider canceling it, thereby reducing the demands of our application and the expectations of our end users.


# Principle 8: Optimization

Completed100 XP

-   3 minutes

Sustainability isn't one optimization, it's thousands. One piece of advice is to look end to end and take it step by step. Often putting in the effort to understand the full stack, from user experience to data center design or electricity grids, yields simple solutions that significantly improve carbon efficiency.

Weigh up the effort required to decarbonize vs. the potential rewards. Just like the broader global sustainability movement, some sectors will be harder to decarbonize than others. In computing, some application domains will be harder to decarbonize than others. Some parts of your application architecture will be harder to decarbonize than others.

The key to success in optimization is to choose a measurement criterion that will give clear signals as to where best to put optimization efforts. For example, is it worthwhile to spend two weeks reducing megabytes from network communication if the database queries cause 10 times more carbon to be emitted?

Rarely can we directly measure our application's carbon cost, but if we follow a resource chain down and it eventually has a link to carbon emissions, then that's a good proxy for carbon.

## Carbon

Measuring emitted carbon is a complex challenge, with parts of the stack that need to be estimated rather than measured, but it's possible with some effort.

Because of the variability of carbon intensity and other dependencies, the total carbon emitted may change depending on the time of day or region the application is run.

The same application measured at different times will result in different amounts of carbon. This change could be a good signal, especially if you're open to demand-shifting workloads, or it could be noise if you're focusing on energy optimizations.

## Energy

The energy your application consumes may vary every time it runs; this change may be something you want to take as an optimization signal, or it may be something you want to control.

The same application run on different hardware may result in different amounts of energy consumed because of the differences in energy efficiency between the hardware components.

Because of the energy proportionality principle, the same application run on the same hardware but at different times may result in different amounts of energy consumed, because the utilization of the hardware is different between the two runs. That is, the hardware might be running other applications during the second run, and this changes the hardware's overall energy efficiency.

Overall, though, creating applications that consume less electricity for the same human-perceptible performance and output is a good proxy for carbon reduction.

There are devices, tools, and libraries available to measure the energy consumed by an application.

## Cost

At some point, the cost of electricity and hardware is factored into most services. Building applications that run as cheaply as possible is usually a good proxy for applications that emit less carbon.

## Networking

The carbon-cost of networking isn't often considered. Networking consumes electricity and requires hardware, so it's a proxy for carbon.

Measuring and then reducing the amount and distance your data must travel is a good proxy for reducing carbon.

## Performance

To build more performant applications is to build applications that utilize hardware and electricity more efficiently. Since hardware and electricity are proxies for carbon, if you can architect an application that performs better for the same level of utilization, this design will likely reduce overall carbon.