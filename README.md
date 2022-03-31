# Interactive EEG
This is a student project trying to visualize common EEG stuff interactivly via [Pluto.jl](https://github.com/fonsp/Pluto.jl). Feel free to contribute with ideas or notebooks as well as correcting me 

## **Files**
- ``/notebooks`` folder containing the notebooks listed below
    - ``deconvolution.jl``
    - ``clusterPermutation.jl``
    - ``filterArtefacts.jl``
    - ``heatmap.jl``
    - ``splineRegression.jl``
- ``PlutoDeployment.toml`` custom configuration of the pluto slider server
- ``Project.toml`` dependencies
- ``export.jl`` script to export the notebooks precomputed as .html-files
- ``start.jl`` script for startup of the pluto slider server


## **Export precomputed notebooks**
- Checkout the branch / pull request [#29](https://github.com/JuliaPluto/PlutoSliderServer.jl/pull/29) (Note that it is still WIP)

- Activate branch of [#29](https://github.com/JuliaPluto/PlutoSliderServer.jl/pull/29) PlutoSliderServer.jl in julia environment of current project 
    ```console
    $ julia --project="."
    ```
    ```console
    julia> ]
    ```
    ```console
    (interactive-eeg) pkg> dev path/to/PlutoSliderServer.jl#29
    ```

- Start precomputing & exporting the slider server by running the following:
    ```console
    julia --project="." export.jl
    ```

## **Starting as pluto slider server**
- If you don't want to precompute the notebooks and simply run them, type the following (Then also the the pull request #29 is not neccessary):
    ```console
    julia --project="." start.jl
    ```

    > **_NOTE:_**  Should work also on the branch #29. But if you want to have the newest PlutoSliderServer.jl you might have to free the package again (if you have used the precomputation branch before).
    julia environment of current project 
    ```console
    $ julia --project="."
    ```
    ```console
    julia> ]
    ```
    ```console
    (interactive-eeg) pkg> free PlutoSliderServer
    ```

## **Additional Notes @Bene**
- I now uploaded the notebooks with the original intended options and sliders. Those "bigger" notebooks still have problems with the precomputation. Even when they are succesfully computed without any erros after some time, some sliders don't work. The minimized versions can still be generated by deleting options later.

- For visual purposes i wanted the legend at some plots in ``deconvolution.jl`` at the bottom. Because the [Plots.jl](https://github.com/JuliaPlots/Plots.jl) plotly() backend was slightly broken, i had to fix some attribute names in the package. The fixed version is located at [Plots.jl](https://github.com/llips/Plots.jl)
