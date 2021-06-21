cmake_minimum_required(VERSION 3.12)

project(Example Fortran)

include(GNUInstallDirs)

# set CMAKE_PREFIX_PATH to the directory containing iriclibConfig.cmake
# ie -DCMAKE_PREFIX_PATH=c:/iricdev/lib/install/iricdev-0.2.9/lib/cmake/iriclib
find_package(iriclib REQUIRED)

# Change this to ON if solver requires OpenMP
option(IRIC_SOLVER_USE_OPENMP "Solver requires OpenMP" ON)
if(IRIC_SOLVER_USE_OPENMP)
  find_package(OpenMP REQUIRED)
endif()

add_executable(Example
  source/add_array_ptoH.f90
  source/add_array_ptoT.f90
  source/add_edge_to_array.f90
  source/adjust_bed_elevation.f90
  source/adjust_water_depth.f90
  source/adjustZb.f90
  source/afe_flux.f90
  source/alloc_err.f90
  source/azimuth2angle.f90
  source/bcs.f90
  source/bed_slope.f90
  source/bed_slope_DFB.f90
  source/bed_slope_ETA.f90
  source/bed_slope_STD.f90
  source/bed_slope_VTX.f90
  source/byebye.f90
  source/c2v_setup.f90
  source/ccstring.f90
  source/cde_t2t.f90
  source/cell_centered.f90
  source/cell_grads.f90
  source/cell_velocity.f90
  source/centered.f90
  source/chan_arrays.f90
  source/constants.f90
  source/correct_vtx.f90
  source/crit_outflow.f90
  source/ctr2vtx.f90
  source/ctr2vtxWSE.f90
  source/cvdisch.f90
  source/cvprep.f90
  source/dataprepFVT.f90
  source/dataprepRDS.f90
  source/deltat.f90
  source/deltatFVT.f90
  source/dep_vars.f90
  source/dirichlet.f90
  source/distribution.f90
  source/drynwet.f90
  source/dump2file.f90
  source/eddy_viscosity.f90
  source/edge_copy.f90
  source/edge_in_array.f90
  source/edge_in_element.f90
  source/edge_normals.f90
  source/elemnt_db.f90
  source/enforce_bcs.f90
  source/equals.f90
  source/err_opts.f90
  source/error_est.f90
  source/errore.f90
  source/fe_flux.f90
  source/find_dry_cells.f90
  source/find_edges.f90
  source/findtt.f90
  source/findttcheck.f90
  source/flood_chan.f90
  source/flux_ac.f90
  source/flux_bgnvc.f90
  source/flux_HLL.f90
  source/flux_rusanov.f90
  source/fnames.f90
  source/free_flow.f90
  source/fric_slope.f90
  source/fric_terms.f90
  source/fric_terms_impl.f90
  source/fvsources.f90
  source/geometry.f90
  source/get_extension.f90
  source/get_iounit.f90
  source/get_time_bcs.f90
  source/grad.f90
  source/gradhordr.f90
  source/hdlsq_grad_array.f90
  source/hdlsq_grad_array4h.f90
  source/hdlsq_setup.f90
  source/header.f90
  source/heffective.f90
  source/hequivalent.f90
  source/hgradfix.f90
  source/hgradfix2.f90
  source/hot_start_ASCII.f90
  source/hot_start_cgns.f90
  source/ibc_arrays.f90
  source/ifname.f90
  source/in_array.f90
  source/in_array2.f90
  source/inflowH.f90
  source/inflowQbyH.f90
  source/initialize_options.f90
  source/integral_md.f90
  source/integral_Ut.f90
  source/invert.f90
  source/invert_edge_dirs.f90
  source/invisc_fluxes.f90
  source/io.f90
  source/ioculvert.f90
  source/ioflow.f90
  source/is_edge.f90
  source/jacobian.f90
  source/kmatrices.f90
  source/lda.f90
  source/limiterBJ.f90
  source/local_edge.f90
  source/lsq_grad_array.f90
  source/lsq_grad_array4h.f90
  source/lsq_gradient.f90
  source/lsq_setup.f90
  source/margins.f90
  source/mem_add.f90
  source/mem_call.f90
  source/memory.f90
  source/mesh_in.f90
  source/mesh_out.f90
  source/narrow.f90
  source/neighbor.f90
  source/node_db.f90
  source/node_in_bdry.f90
  source/node_in_triang.f90
  source/nonlinearb.f90
  source/npoints.f90
  source/options.f90
  source/outflowbyH.f90
  source/outflowbyH2.f90
  source/outflowbyH3.f90
  source/output_data.f90
  source/output_dataV.f90
  source/overdraft.f90
  source/parameters.f90
  source/part_dry.f90
  source/phisubt.f90
  source/positivity_vtx.f90
  source/probefileh.f90
  source/probefileo.f90
  source/pto_in_edge.f90
  source/pto_in_triangle.f90
  source/query.f90
  source/read_cgns.f90
  source/read_data.f90
  source/read_mfa.f90
  source/read_options.f90
  source/readline.f90
  source/readp.f90
  source/residuals.f90
  source/RKparams.f90
  source/rmv_array_pto.f90
  source/rvegdata.f90
  source/select_out.f90
  source/Shields_diameter.f90
  source/Shields_tau.f90
  source/skin_friction.f90
  source/solver.f90
  source/solverFVT.f90
  source/solverRDS.f90
  source/sortEdges.f90
  source/spit_out.f90
  source/storm.f90
  source/strip_ext.f90
  source/t_areas.f90
  source/tecplot.f90
  source/tecplot_read.f90
  source/tecplot_write.f90
  source/to_upper.f90
  source/to_vertices.f90
  source/vbc_arrays.f90
  source/vbc_by_h.f90
  source/vcrop.f90
  source/visc_fluxes.f90
  source/visc_terms.f90
  source/viscosity.f90
  source/vtx2ctr.f90
  source/walls.f90
  source/wenslp2_fluxes.f90
  source/wenslp3_fluxes.f90
  source/wenslp_fluxes.f90
  source/weslp2_fluxes.f90
  source/weslp3_fluxes.f90
  source/weslp_fluxes.f90
  source/wetdryfix.f90
  source/wetdryvfix.f90
  source/windforcing.f90
  source/windforcing2.f90
  source/write_cgns.f90
  source/write_cgns_cblock.f90
  source/write_cgns_cell.f90
  source/zeta_bcs.f90
)

target_link_libraries(Example PRIVATE iriclib::iriclib)

if(IRIC_SOLVER_USE_OPENMP AND OpenMP_Fortran_FOUND)
  target_link_libraries(Example PRIVATE OpenMP::OpenMP_Fortran)
endif()

install(TARGETS Example DESTINATION "${CMAKE_INSTALL_BINDIR}")

install(FILES <LOCATION OF definition.xml> DESTINATION "${CMAKE_INSTALL_BINDIR}")

# include(CTest)

# add_subdirectory(tests)
