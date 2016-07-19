# e-MUSC Glossary

This document contains a collection of terms relevant to the e-MUSC project, with definitions or descriptions and references as appropriate. It's an informal collection of notes, to be used for gathering our thoughts and as a quick reference, and not intended to be a citable resource.


* COAST
    - Project in which the theory of Complex Automata (CxA) was developed. The Multiscale Modelling Language (MML) and Distributed Space Time Coupling Library (DSTC) originated here. http://www.complex-automata.org

* Complex Automata
    - Paradigm in which multiple single-scale cellular automata are coupled to form a multi-scale model.

* Coupling Template

* Distributed Multiscale Computing (DMC)
    - The combination of multi-scale modelling and distributed computing. See also Tied Multiscale Computing, Skewed Multiscale Computing and Scalable Multiscale Computing.

* Distributed Space Time Coupling Library (DSTC)
    - Library for coupling multiscale cellular automata; predecessor of MUSCLE

* Hierarchical Multiscale Method (HMM)
    - Method for decomposing a multi-scale model into single-scale submodels.

* In-stent Restenosis
    - The process in which a stenosis (clogging of artery) reappears after a stent has been placed in the artery to keep it open. This occurs in some patients, apparently as a result of injury to the artery caused by the stent. Why this happens and how it's affected by the shape of the stent, and by the effect of the blood-diluting drugs it's coated in, is unknown, and therefore worthy of modelling. Note that it's re-stenosis, not res-tenosis. See ISR3D.

* ISR3D
    - A 3D model of in-stent restenosis, successor of ISR2D. ISR3D comprises a CFD (Lattice Boltzmann) blood flow model, ...

* MAPPER
    - Project in which a theory of multi-scale modelling was developed, generalising from and building on Complex Automata theory and the COAST project. http://www.mapper-project.eu

* MML

* Multiscale modelling
    - The process of making models by connecting separate, single-scale submodels.


* MUltiscale Coupling Library and Environment 2 (MUSCLE 2)
    - A library for coupling in multiscale models. Developed by Joris Borgdorff as part of the European MAPPER project. http://apps.man.poznan.pl/trac/muscle

* QosCosGrid (QCG)

* Scale
    - A scale is an order of magnitude along a coordinate. A scale is defined by a minimum (δ) and maximum(Δ) granularity and a minimum (ω) and maximum (Ω) total size. A scale is *regular* if δ = Δ and ω = Ω. A regular scale is *point* if Δ = Ω. See Borgdorff, J. Distributed Multiscale Computing.

* Scale separation (Borgdorff)
    - Scales s = (δ, Δ, ω, Ω) and s' = (δ', Δ', ω', Ω') with Ω > Ω' or if Ω = Ω' then Δ > Δ' are
        + overlapping iff Δ < ω' and Δ' < ω
        + separated iff Ω' < δ
        + contiguous iff Δ' ≤ δ ≤ Ω' ≤ Δ
    - Note on interpretation, assuming temporal scales (L. Veen)
        + s and s' are overlapping if all of these are true:
            - Every run of s' will have at least one tick of s during it
            - Every run of s will have at least one tick of s' during it
        + s and s' are separated if
            - Each run of s' fits between any two ticks of s
        + s and s' are contiguous if all of these are true:
            - All steps of s' are smaller than all steps of s
            - The longest run time of s' is within the step size range of s
        + if s and s' are both regular and contiguous, then the time step of s equals the total run time of s', and the step size of s' must be smaller than or equal to that

* Scale Separation Map (SSM)
    - A log-log plot in which spatial and temporal scales of a (sub)model are shown using boxes.

* Submodel Execution Loop (SEL)
    - The SEL is a generalised model of a submodel in the context of multi-scale modelling. It is used as a basis for defining coupling templates. According to the SEL, a submodel performs the following steps:
        + i ← 0
        + f, θ ← **f_init**(t0)
        + while |θ[i]| > 0 do
            + **O_i**(f, t(e[i]), t(e[i+1])
            + i ← i + 1
            + f, θ[i] ← **S**(f, e[i], θ[i])
            + f, θ[i] ← **B**(f, e[i], θ[i])
        + end
        + **O_f**(f, t(e[i]))

      Where f is the current state of the model, i the current iteration, θ[i] the model time corresponding to the i'th iteration, e[i] the current event, and **f_init**, **S**, **B**, **O_i** and **O_f** are operators. **f_init** initialises the state, **S** performs a state update, **B** updates the boundary conditions, **O_i** observes the state at model iteration i, and **O_f** observes the final state at the end of the model run. **f_init**, **S** and **B** can take input from outside of the submodel, while **O_i** and **O_f** produce output that can be sent to other submodels. See Coupling Templates for more.


