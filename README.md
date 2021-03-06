# Interactive EEG
This is a student project trying to visualize common EEG stuff interactivly via [Pluto.jl](https://github.com/fonsp/Pluto.jl). Feel free to contribute with ideas or notebooks as well as correcting me at places where i made mistakes. Thanks :)

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


## **Develop and interact in current state with all sliders**
- Start pluto in the directory of the git repository and open the notebooks in Pluto
    ```console
    $ julia --project="."
    ```
    ```console
    julia> using Pluto
    julia> Pluto.run()
    ``` 



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
    $ julia --project="." export.jl
    ```

## **Starting as pluto slider server**
- If you don't want to precompute the notebooks and simply run them, type the following (Then also the the pull request #29 is not neccessary):
    ```console
    $ julia --project="." start.jl
    ```

    > **_NOTE:_**  Should work also on the branch #29. But if you want to have the newest PlutoSliderServer.jl you might have to free the package again (if you have used the precomputation branch before).
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
- I now uploaded the notebooks for the submission with all the original intended options and sliders. Those files are to big to be precomputed because of too many options. The minimized versions can still be generated by deleting possible options in the case of the notebook ``filterArtefacts.jl``.
  - ``deconvolution.jl`` : Limiting sliders b, d to 1 value as well as the selection of functions to two. Additionally the slider for the window size has to be deleted. After that the precomputation succesfully runs through but some sliders still don't work.
  - ``clusterPermutationTest.jl`` : Still can be precomputed.
  - ``filterArtefacts.jl``: Deleting sliders/options freq, noise & limiting the filter methods. 

- For visual purposes i wanted the legend at some plots in ``deconvolution.jl`` at the bottom. Because the [Plots.jl](https://github.com/JuliaPlots/Plots.jl) plotly() backend was slightly broken, i had to fix some attribute names in the package. The fixed version is located at [Plots.jl](https://github.com/llips/Plots.jl). A consequence of this is that for the ``deconvolution.jl`` the internal notebook environment / package manager is deactivated. And i am not sure if i have to include the packages therefore in the ``Project.toml`` (For me it still worked in the "new" environment.
