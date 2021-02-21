List of cell properties
======================================================================================

All cell properties are proportional to a unit grid according to lattice dimensionality
(*e.g.*, for unit length *x* in a 3-dimensional regular lattice, ``cell.volume`` and ``cell.surface``
have dimensions *x*\ :sup:`3` and *x*\ :sup:`2`, respectively):

.. csv-table::
    :header: "Name", "Attribute", "Modifiable?", "Comments"
    :widths: 30, 50, 22, 65

    Cell identity, ``id``, No, Unique cell identification number
    Cell type, ``type``, Yes, Integer indicating the cell type
    Cell volume, ``volume``, No, Instantaneous cell volume
    [#f1]_, ``targetVolume``, Yes, Target value of volume constraint
    [#f1]_, ``lambdaVolume``, Yes, Lambda of the volume constraint
    Cell surface [#f2]_, ``surface``, No, Instantaneous cell surface
    , ``targetSurface``, Yes, Target value of surface constraint
    , ``lambdaSurface``, Yes, Lambda of the surface constraint
    Center of mass [#f3]_, ``xCOM``, No, Cartesian coordinate *x* of center of mass
    , ``yCOM``, No, Cartesian coordinate *y* of center of mass
    , ``zCOM``, No, Cartesian coordinate *z* of center of mass
    Eccentricity [#f4]_, ``ecc``, No, Eccentricity of cell
    Inertia tensor [#f4]_, ``iXX``, No, Moment of inertia *x*-axis about the *x*-axis
    , ``iYY``, No, Moment of inertia *y*-axis about the *y*-axis
    , ``iZZ``, No, Moment of inertia *z*-axis about the *z*-axis
    , ``iXY``, No, Moment of inertia *x*-axis about the *y*-axis
    , ``iXZ``, No, Moment of inertia *x*-axis about the *z*-axis
    , ``iYZ``, No, Moment of inertia *y*-axis about the *z*-axis
    Minor axis vector [#f4]_, ``lX``, No, Component *x* of vector along semiminor axis
    , ``lY``, No, Component *y* of vector along semiminor axis
    , ``lZ``, No, Component *z* of vector along semiminor axis
    Directional forces [#f5]_, ``lambdaVecX``, Yes, Force component acting on the *x*-direction
    , ``lambdaVecY``, Yes, Force component acting on the *y*-direction
    , ``lambdaVecZ``, Yes, Force component acting on the *z*-direction
    Cell internal pressure [#f1]_, ``pressure``, No, Instantaneous internal pressure
    Cell surface tension [#f2]_, ``surfaceTension``, No, Instantaneous surface tension
    Cluster surface tension [#f2]_, ``clusterSurfaceTension``, No, Surface tension of cluster

.. footnotes::csv-table
.. [#f1] Only available when ``Volume`` plugin is loaded and parameters are assigned per cell
    in a steppable (rather than in CC3DML)
.. [#f2] Only available when ``Surface`` , ``SurfaceTracker``, ``SurfaceFlex`` or ``SurfaceLocalFlex`` plugins are loaded.
.. [#f3] Only available when ``CenterOfMass`` plugin is loaded.
.. [#f4] Only available when ``MomentOfInertia`` plugin is loaded.
.. [#f5] Only available when ``ExternalPotential`` plugin is loaded.

