List of cell properties
======================================================================================

All cell properties are proportional to a unit grid according to lattice dimensionality
(*e.g.*, for unit length *x* in a 3-dimensional regular lattice, ``cell.volume`` and ``cell.surface``
have dimensions *x*\ :sup:`3` and *x*\ :sup:`2`, respectively):

.. csv-table::
    :header: "Name", "Command", "Modifiable?", "Comments"
    :widths: 30, 40, 20, 65

    Cell identity, ``cell.id``, No, Unique cell identification number
    Cell type, ``cell.type``, Yes, Integer indicating the cell type
    Cell volume, ``cell.volume``, No, Instantaneous cell volume
    [#f1]_, ``cell.targetVolume``, Yes, Target value of volume constraint
    [#f1]_, ``cell.lambdaVolume``, Yes, Lambda of the volume constraint
    Cell surface [#f2]_, ``cell.surface``, No, Instantaneous cell surface
    , ``cell.targetSurface``, Yes, Target value of surface constraint
    , ``cell.lambdaSurface``, Yes, Lambda of the surface constraint
    Center of mass [#f3]_, ``cell.xCOM``, No, Cartesian coordinate *x* of center of mass
    , ``cell.yCOM``, No, Cartesian coordinate *y* of center of mass
    , ``cell.zCOM``, No, Cartesian coordinate *z* of center of mass
    Eccentricity [#f4]_, ``cell.ecc``, No, Eccentricity of cell
    Inertia tensor [#f4]_, ``cell.iXX``, No, Moment of inertia *x*-axis about the *x*-axis
    , ``cell.iYY``, No, Moment of inertia *y*-axis about the *y*-axis
    , ``cell.iZZ``, No, Moment of inertia *z*-axis about the *z*-axis
    , ``cell.iXY``, No, Moment of inertia *x*-axis about the *y*-axis
    , ``cell.iXZ``, No, Moment of inertia *x*-axis about the *z*-axis
    , ``cell.iYZ``, No, Moment of inertia *y*-axis about the *z*-axis
    Minor axis vector [#f4]_, ``cell.lX``, No, Component *x* of vector along semiminor axis
    , ``cell.lY``, No, Component *y* of vector along semiminor axis
    , ``cell.lZ``, No, Component *z* of vector along semiminor axis
    Directional forces [#f5]_, ``cell.lambdaVecX``, Yes, Force component acting on the *x*-direction
    , ``cell.lambdaVecY``, Yes, Force component acting on the *y*-direction
    , ``cell.lambdaVecZ``, Yes, Force component acting on the *z*-direction

.. footnotes::csv-table
.. [#f1] Only available when ``Volume`` plugin is loaded and parameters are assigned per cell
    in a steppable (rather than in CC3DML)
.. [#f2] Only available when ``Surface`` , ``SurfaceTracker``, ``SurfaceFlex`` or ``SurfaceLocalFlex`` plugins are loaded.
.. [#f3] Only available when ``CenterOfMass`` plugin is loaded.
.. [#f4] Only available when ``MomentOfInertia`` plugin is loaded.
.. [#f5] Only available when ``ExternalPotential`` plugin is loaded.

