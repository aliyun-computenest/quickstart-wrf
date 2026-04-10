<h1>WRF Ehpc Compute Nest Quick Deployment</h1>

<blockquote>
    <p><strong>Disclaimer:</strong> This service is provided by a third party. We strive to ensure its security, accuracy, and reliability, but we cannot guarantee that it will be completely free from failures, interruptions, errors, or attacks. Therefore, our company hereby declares: we make no representations, warranties, or commitments regarding the content, accuracy, completeness, reliability, applicability, or timeliness of this service, and we assume no liability for any direct or indirect losses or damages arising from your use of this service; we assume no liability for the content, accuracy, completeness, reliability, applicability, or timeliness of third-party websites, applications, products, and services accessed by you through this service, and you shall bear the risks and responsibilities arising from the consequences of such use; we assume no liability for any losses or damages arising from your use of this service, including but not limited to direct losses, indirect losses, loss of profits, loss of goodwill, data loss, or other economic losses, even if our company has been informed in advance of the possibility of such losses or damages; we reserve the right to modify this statement from time to time, so please check this statement regularly before using this service. If you have any questions or concerns about this statement or this service, please contact us.</p>
</blockquote>

<h2>Overview</h2>

<p>WRF (Weather Research and Forecasting) adopts a new generation of mesoscale weather forecasting models and is an open-source meteorological simulation software widely used in the meteorological industry. It provides numerous options for studying atmospheric processes and can run on various computing platforms.</p>

<h2>Prerequisites</h2>

<p>To deploy the WRF Community Edition service instance, you need to access and create certain Alibaba Cloud resources. Therefore, your account requires permissions for the following resources.</p>
<p><strong>Note:</strong> Permissions need to be added only if your account is a RAM user.</p>

<table>
    <thead>
        <tr>
            <th>Permission Policy Name</th>
            <th>Remarks</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>AliyunECSFullAccess</td>
            <td>Permission to manage Elastic Compute Service (ECS)</td>
        </tr>
        <tr>
            <td>AliyunVPCFullAccess</td>
            <td>Permission to manage Virtual Private Cloud (VPC)</td>
        </tr>
        <tr>
            <td>AliyunROSFullAccess</td>
            <td>Permission to manage Resource Orchestration Service (ROS)</td>
        </tr>
        <tr>
            <td>AliyunEHPCFullAccess</td>
            <td>Permission to manage Elastic High Performance Computing (EHPC)</td>
        </tr>
        <tr>
            <td>AliyunNASFullAccess</td>
            <td>Permission to manage File Storage (NAS)</td>
        </tr>
        <tr>
            <td>AliyunComputeNestUserFullAccess</td>
            <td>User-side permissions to manage Compute Nest services</td>
        </tr>
    </tbody>
</table>

<h2>Billing Description</h2>

<p>The costs for deploying the WRF Community Edition on Compute Nest mainly involve:</p>
<ul>
    <li>Elastic High Performance Computing Cluster (EHPC) fees</li>
    <li>File System (NAS) fees</li>
    <li>Traffic bandwidth fees</li>
</ul>

<h2>Deployment Architecture</h2>

<ul>
    <li>The deployment consists of one EHPC cluster, which includes manager nodes, scheduler nodes, and compute nodes.</li>
    <li>The service uses NAS-CPFS to build a high-performance shared file system.</li>
</ul>

<h2>Parameter Description</h2>

<table>
    <thead>
        <tr>
            <th>Parameter Group</th>
            <th>Parameter Item</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="3">Service Instance</td>
            <td>Service Instance Name</td>
            <td>No more than 64 characters. Must start with an English letter. Can contain numbers, English letters, hyphens (-), and underscores (_).</td>
        </tr>
        <tr>
            <td>Region</td>
            <td>The region where the service instance is deployed.</td>
        </tr>
        <tr>
            <td>Payment Type</td>
            <td>Billing type for resources: Pay-As-You-Go and Subscription.</td>
        </tr>
        <tr>
            <td rowspan="6">EHPC Cluster Configuration</td>
            <td>Cluster Login Password</td>
            <td>Length 8-30 characters. Must contain at least three of the following: uppercase letters, lowercase letters, numbers, and special symbols ()`~!@#$%^&*-+=|{}[]:;'&lt;&gt;,.?/</td>
        </tr>
        <tr>
            <td>EHPC Deployment Mode</td>
            <td>Tiny, Simple, Standard</td>
        </tr>
        <tr>
            <td>Compute Node Instance Type</td>
            <td>Available compute node specifications in the availability zone.</td>
        </tr>
        <tr>
            <td>Number of Compute Nodes</td>
            <td>Number of compute nodes. Optional values: 1-99.</td>
        </tr>
        <tr>
            <td>Login Node Instance Type</td>
            <td>Available login node specifications in the availability zone.</td>
        </tr>
        <tr>
            <td>Number of Management Nodes</td>
            <td>Number of management nodes. Optional values: 1, 2, 4.</td>
        </tr>
        <tr>
            <td rowspan="2">EHPC Cluster User Configuration</td>
            <td>User Password</td>
            <td>Length 8-30 characters. Must contain at least three of the following: uppercase letters, lowercase letters, numbers, and special symbols ()~!@#$%^&*-_+=\{}[]:;'/&lt;&gt;,.?/</td>
        </tr>
        <tr>
            <td>Username</td>
            <td>The username used to log in to the cluster. Default is "lammps".</td>
        </tr>
        <tr>
            <td rowspan="3">Network Configuration</td>
            <td>Availability Zone</td>
            <td>The availability zone where the ECS instances are located.</td>
        </tr>
        <tr>
            <td>VPC ID</td>
            <td>The VPC where the resources are located.</td>
        </tr>
        <tr>
            <td>VSwitch ID</td>
            <td>The vSwitch where the resources are located.</td>
        </tr>
    </tbody>
</table>

<h2>Deployment Process</h2>

<ol>
    <li>
        <p>Visit the Compute Nest WRF Community Edition <a href="https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-f38983a8f42b479b8f9c" target="_blank">deployment link</a>.</p>
    </li>
    <li>
        <p>After filling in the parameters, you will see the corresponding price inquiry details. Confirm the parameters and click <strong>Next: Confirm Order</strong>.</p>
    </li>
    <li>
        <p>After confirming the order, agree to the service agreement and click <strong>Create Now</strong>. The deployment phase begins.</p>
    </li>
</ol>

<h2>Usage Process</h2>

<h3>Step 1: Connect to the Cluster via Console</h3>

<ol>
    <li>Log in to the <a href="https://ehpc.console.aliyun.com" target="_blank">Elastic High Performance Computing Console</a>.</li>
    <li>In the top menu bar, select the region in the upper left corner.</li>
    <li>In the left navigation pane, click <strong>Clusters</strong>.</li>
    <li>On the <strong>Clusters</strong> page, find the target cluster deployed via Compute Nest and click <strong>Remote Connection</strong>.</li>
    <li>On the <strong>Remote Connection</strong> page, enter the cluster username, login password, and port, then click <strong>SSH Connection</strong>.</li>
</ol>

<h3>Step 2: Submit Jobs</h3>

<p>This section describes how to run WRF software for meteorological simulation calculations on an E-HPC cluster.</p>

<ol>
    <li>
        <p>Check if WRF-related software is installed on the cluster.</p>
        <pre><code>export MODULEPATH=/opt/ehpcmodulefiles/
module avail</code></pre>
        <p>Expected output:</p>
        <pre><code>----------------------------- /opt/ehpcmodulefiles/ ------------------------
mpich/3.2       vnc             wrf-mpich/3.8.1</code></pre>
    </li>
    <li>
        <p>Load the WRF software environment.</p>
        <pre><code>module load wrf-mpich/3.8.1 mpich/3.2
echo $WPSHOME $WRFHOME</code></pre>
    </li>
    <li>
        <p>Copy the installed WPS and WRF software to the working directory.</p>
        <blockquote>
            <p><strong>Note:</strong> Replace <code>$WPSCOPYHOME</code> and <code>$WRFCOPYHOME</code> in the commands with the actual working directory. This example uses <code>/home/wrftest</code>. After execution, two directories, WPS and WRFV3, will be generated in this directory.</p>
        </blockquote>
        <pre><code>cp -r $WPSHOME /home/wrftest
cp -r $WRFHOME /home/wrftest</code></pre>
    </li>
    <li>
        <p>Enter the WPS directory, then download and extract surface data.</p>
        <blockquote>
            <p><strong>Note:</strong> This example uses <code>geog_complete.tar.gz</code> for surface data. You can download other surface data as needed.</p>
        </blockquote>
        <pre><code>cd /home/wrftest/WPS
wget https://www2.mmm.ucar.edu/wrf/src/wps_files/geog_complete.tar.gz
tar -zxvf geog_complete.tar.gz</code></pre>
    </li>
    <li>
        <p>Create a symbolic link to the GEOGRID.TBL file.</p>
        <blockquote>
            <p><strong>Note:</strong> The GEOGRID.TBL file defines the static geographic dataset parameters that geogrid.exe needs to interpolate onto grid points.</p>
        </blockquote>
        <pre><code>ln -s geogrid/GEOGRID.TBL GEOGRID.TBL</code></pre>
    </li>
    <li>
        <p>Modify the <code>namelist.wps</code> file.</p>
        <p>namelist is a shared file in WPS (WRF Preprocessing System). It is divided into three parts (&amp;geogrid, &amp;ungrib, &amp;metgrid) and one shared part (&amp;share) based on the parameters required by different programs (geogrid.exe, ungrib.exe, metgrid.exe), defining various parameters required by the WPS modules. The following is a recommended configuration; keep default values for parameters not mentioned.</p>
        <blockquote>
            <ol>
                <li>In this example, the namelist.wps file is located in the <code>/home/wrftest/WPS</code> directory.</li>
                <li>In the namelist.wps file, use <code>!</code> as the comment identifier.</li>
            </ol>
        </blockquote>
        <pre><code>! Shared Part
&share   
! wrf_core: Select WRF dynamical core, options are 'ARW' and 'NMM', default is 'ARW'.
wrf_core = 'ARW', 
! start_date: Simulation start time
start_date = '2005-08-28_00:00:00',  
! end_date: Simulation end time
end_date = '2005-08-29_00:00:00',     
interval_seconds = 21600,
! max_dom: Number of simulation grids (coarse grid + nested grids), this example contains one coarse grid
max_dom = 1, 
! #io_form_geogrid: Output format for geogrid program
io_form_geogrid = 2,    
/

! geogrid Part
! # Determine area range, nesting relationship, model projection
&geogrid
parent_id = 1,
parent_grid_ratio = 1,
i_parent_start = 1,
j_parent_start = 1,

! Determine grid scale in east-west and north-south directions (number of raster cells for vector fields in the area), this example is 98*70 grid points
e_we = 98,       
e_sn = 70,
geog_data_res = 'default',

! Define grid cell size for the area, this example grid resolution is 30km
dx = 30000,     
dy = 30000,

! Define projection method, refer to WRF official website for projection details
map_proj = 'mercator'

! Define center latitude and longitude coordinates of the area
ref_lat = 25.00,
ref_lon = -89.00,

! Three projection parameter values, set differently depending on projection method
truelat1 = 0.0,   
truelat2 = 0.0,
stand_lon = -89.0,
! geog_data_path = 'Path to surface data storage'
geog_data_path = '/home/wrftest/WPS/geog'
/

! ungrib Part
&ungrib
! out_format: File format generated by ungrib readable by metgrid, options are 'WPS', 'SI', 'MM5', default is 'WPS'
out_format = 'WPS', 
! prefix: Path and file prefix for intermediate files generated by ungrib
prefix = 'FILE'
/
 
! metgrid Part 
&metgrid  
! fg_name: Files generated by ungrib program
fg_name = 'FILE', 
! io_form_metgrid: File format generated by metgrid
! Supports three formats: 1 (binary, suffix .int), 2 (netCDF, suffix .nc), 3 (Grib1, suffix .gr1)
! Default: 2
io_form_metgrid = 2
/</code></pre>
    </li>
    <li>
        <p>Interpolate static terrain data to grid points.</p>
        <pre><code>./geogrid.exe</code></pre>
        <p>After successful execution of geogrid.exe, the geo_em.d0N.nc terrain file will be generated in the <code>/home/wrftest/WPS</code> directory.</p>
    </li>
</ol>

<h3>Step 3: Run ungrib.exe</h3>

<p>ungrib.exe is used to extract required meteorological element fields from GRIB format meteorological data.</p>

<ol>
    <li>
        <p>Download and extract Katrina meteorological data.</p>
        <blockquote>
            <p><strong>Note:</strong> This example uses <code>Katrina.tar.gz</code> for meteorological data. Please download Katrina.tar.gz. You can also download other meteorological data as needed.</p>
        </blockquote>
        <pre><code>cd /home/wrftest/WPS
wget http://www2.mmm.ucar.edu/wrf/TUTORIAL_DATA/Katrina.tar.gz
tar -zxvf Katrina.tar.gz</code></pre>
    </li>
    <li>
        <p>Link meteorological data using the link_grib.csh script.</p>
        <pre><code>./link_grib.csh /home/wrftest/WPS/Katrina/avn*</code></pre>
    </li>
    <li>
        <p>Select the corresponding Vtable for the meteorological data.<br>
        This example uses Vtable.GFS. You can use other Vtables as needed.</p>
        <pre><code>ln -sf ungrib/Variable_Tables/Vtable.GFS Vtable</code></pre>
    </li>
    <li>
        <p>Extract the required meteorological element fields.</p>
        <pre><code>./ungrib.exe</code></pre>
        <p>After successful execution of ungrib.exe, FILE:YYYY-MM-DD_hh* files will be generated in the <code>/home/wrftest/WPS</code> directory.</p>
    </li>
</ol>

<h3>Step 4: Run metgrid.exe</h3>

<p>metgrid.exe is used to horizontally interpolate the meteorological field data extracted by ungrib.exe onto the grid points determined by geogrid.exe.</p>

<ol>
    <li>
        <p>Create a symbolic link to the METGRID.TBL file.</p>
        <p>The METGRID.TBL file defines how metgrid.exe horizontally interpolates meteorological data onto grid points.</p>
        <pre><code>cd /home/wrftest/WPS
ln -s metgrid/METGRID.TBL.ARW METGRID.TBL</code></pre>
    </li>
    <li>
        <p>Horizontally interpolate meteorological field data onto the grid points determined by geogrid.</p>
        <pre><code>./metgrid.exe</code></pre>
        <p>After successful execution of metgrid.exe, met_em.d0N.yyyy-mm-dd_hh:mm:ss.nc files will be generated in the <code>/home/wrftest/WPS</code> directory.</p>
    </li>
</ol>

<h3>Step 5: Run wrf.exe</h3>

<p>wrf.exe is used to output weather prediction data.</p>

<ol>
    <li>
        <p>Link WPS processing results.</p>
        <pre><code>cd /home/wrftest/WRFV3
ln -s /home/wrftest/WPS/met_em.d01.2005-08-2*.</code></pre>
        <blockquote>
            <p><strong>Note:</strong> If the linking fails here, the wrfinput_d01 and wrfbdy_d01 files will not be created later. You can copy the files starting with met_em.d01.2005-08-2 from the <code>/home/wrftest/WPS</code> folder to the <code>/home/wrftest/WRFV3</code> folder.</p>
        </blockquote>
    </li>
    <li>
        <p>Modify the namelist.input file.</p>
        <pre><code>cd /home/wrftest/WRFV3/run
vim namelist.input</code></pre>
        <p>The parameters in the &amp;time_control and &amp;domains sections of the namelist.input file must match those in the namelist.wps file. The configuration example used in this document is as follows:</p>
        <pre><code>&time_control
run_days                            = 0,
run_hours                           = 12,
run_minutes                         = 0,
run_seconds                         = 0,
start_year                          = 2005, 2005, 2005,
start_month                         = 08,   08,   08,
start_day                           = 28,   28,   28,
start_hour                          = 00,   00,   00,
start_minute                        = 00,   00,   00,
start_second                        = 00,   00,   00,
end_year                            = 2005, 2005, 2005,
end_month                           = 08,   08,   08,
end_day                             = 29,   29,   29,
end_hour                            = 00,   00,   00,
end_minute                          = 00,   00,   00,
end_second                          = 00,   00,   00,
interval_seconds                    = 21600
input_from_file                     = .true.,.true.,.true.,
history_interval                    = 180,  60,   60,
frames_per_outfile                  = 1000, 1000, 1000,
restart                             = .false.,
restart_interval                    = 5000,
io_form_history                     = 2
io_form_restart                     = 2
io_form_input                       = 2
io_form_boundary                    = 2
debug_level                         = 0
iofields_filename                   = "extraoutput_d01.txt"
/

&domains
time_step                           = 180,
time_step_fract_num                 = 0,
time_step_fract_den                 = 1,
max_dom                             = 1,
e_we                                = 98,    112,   94,
e_sn                                = 70,    97,    91,
e_vert                              = 30,    30,    30,
p_top_requested                     = 5000,
num_metgrid_levels                  = 27,
num_metgrid_soil_levels             = 4,
dx                                  = 30000, 10000,  3333.33,
dy                                  = 30000, 10000,  3333.33,
grid_id                             = 1,     2,     3,
parent_id                           = 0,     1,     2,
i_parent_start                      = 1,     31,    30,
j_parent_start                      = 1,     17,    30,
parent_grid_ratio                   = 1,     3,     3,
parent_time_step_ratio              = 1,     3,     3,
feedback                            = 1,
smooth_option                       = 0,
/

&physics
mp_physics                          = 6,     6,     6,
ra_lw_physics                       = 4,     4,     4,
ra_sw_physics                       = 4,     4,     4,
radt                                = 10,    10,    10,
sf_sfclay_physics                   = 1,     1,     1,
sf_surface_physics                  = 2,     2,     2,
bl_pbl_physics                      = 1,     1,     1,
bldt                                = 0,     0,     0,
cu_physics                          = 0,     0,     0,
cudt                                = 0,     0,     0,
isfflx                              = 1,
ifsnow                              = 0,
icloud                              = 1,
surface_input_source                = 1,
num_soil_layers                     = 4,
sf_urban_physics                    = 0,     0,     0,
/



&fdda
/

&dynamics
w_damping                           = 0,
diff_opt                            = 1,      1,      1,
km_opt                              = 4,      4,      4,
diff_6th_opt                        = 0,      0,      0,
diff_6th_factor                     = 0.12,   0.12,   0.12,
base_temp                           = 290.
damp_opt                            = 0,
zdamp                               = 5000.,  5000.,  5000.,
dampcoef                            = 0.2,    0.2,    0.2
khdif                               = 0,      0,      0,
kvdif                               = 0,      0,      0,
non_hydrostatic                     = .true., .true., .true.,
moist_adv_opt                       = 1,      1,      1,     
scalar_adv_opt                      = 1,      1,      1,     
/

&bdy_control
spec_bdy_width                      = 5,
spec_zone                           = 1,
relax_zone                          = 4,
specified                           = .true., .false.,.false.,
nested                              = .false., .true., .true.,
/

&grib2
/

&namelist_quilt
nio_tasks_per_group = 0,
nio_groups = 1,
/</code></pre>
    </li>
    <li>
        <p>Initialize simulation data.</p>
        <pre><code>./real.exe</code></pre>
        <p>After successful execution of real.exe, wrfinput_d01 and wrfbdy_d01 files will be generated in the <code>/home/wrftest/WRFV3/run</code> directory.</p>
    </li>
    <li>
        <p>Output weather prediction data.</p>
        <p>Create a job script:</p>
        <pre><code>vim wrf.slurm</code></pre>
        <p>Example content for wrf.slurm:</p>
        <pre><code>#!/bin/bash
#SBATCH -N 1
#SBATCH -n 2
#SBATCH --cpus-per-task=1
#SBATCH -J wrf-test
#SBATCH -o wrf_test.log

module load wrf-mpich/3.8.1 mpich/3.2
mpirun -np 2 -ppn 1  -bind-to core:1 /home/wrftest/WRFV3/run/wrf.exe</code></pre>
        <p>Submit the job:</p>
        <pre><code>batch &lt; wrf.slurm</code></pre>
        <blockquote>
            <p><strong>Note:</strong> If execution fails, check the wrf_test.log file. If the following error occurs, execute: <code>export LD_LIBRARY_PATH=/opt/WRF_WPS-mpich-3.8.1/util/lib:$LD_LIBRARY_PATH</code></p>
        </blockquote>
        <p>After the job runs successfully, wrfout_d01_[date] files will be generated in the <code>/home/wrftest/WRFV3/run</code> directory, for example: wrfout_d01_2005-08-28_00:00:00.</p>
    </li>
</ol>

<h3>Step 6: Install NCL</h3>

<p>The following are steps to install Miniconda and NCL on CentOS 7.6:</p>

<ol>
    <li>
        <p>Create an ncl folder.</p>
        <pre><code>cd /home/wrftest/WRFV3/run
mkdir ncl</code></pre>
    </li>
    <li>
        <p>Download the Miniconda installation script. You can download the latest version from the Miniconda official website using the following command:</p>
        <pre><code>wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh</code></pre>
    </li>
    <li>
        <p>Run the installation script to install Miniconda. Use the following command to run the script:</p>
        <pre><code>bash Miniconda3-latest-Linux-x86_64.sh</code></pre>
    </li>
    <li>
        <p>Refresh environment variables. "(base)" should appear at the beginning of the prompt.</p>
        <pre><code>source ~/.bashrc</code></pre>
    </li>
    <li>
        <p>Check the installed conda version.</p>
        <pre><code>conda -V</code></pre>
    </li>
    <li>
        <p>Update conda. Answer "yes" to all yes/no prompts.</p>
        <pre><code>conda update -n root --all</code></pre>
    </li>
    <li>
        <p>Install ncl.</p>
        <pre><code>conda create -n ncl_stable -c conda-forge ncl</code></pre>
    </li>
    <li>
        <p>Enter ncl interactive mode.</p>
        <pre><code>conda activate ncl_stable
ncl</code></pre>
        <blockquote>
            <p><strong>Note:</strong> If "ncl 0&gt;" appears on the screen after entering the ncl command, the installation is successful.</p>
        </blockquote>
    </li>
    <li>
        <p>Exit interactive mode.</p>
        <pre><code>exit</code></pre>
    </li>
</ol>

<h3>Step 7: Visualize WRF Results</h3>

<ol>
    <li>
        <p>Create an ncl file.</p>
        <p>Convert the results from Step 5 into an .ncl file.</p>
        <pre><code>cd /home/wrftest/WRFV3/run
vim wrf_test.ncl</code></pre>
        <p>Write the following content into the wrf_test.ncl file:</p>
        <pre><code> load "$NCARG_ROOT/lib/ncarg/nclscripts/csm/gsn_code.ncl" 
 load "$NCARG_ROOT/lib/ncarg/nclscripts/wrf/WRFUserARW.ncl"
begin 
  a = addfile("/home/wrftest/WRFV3/run/wrfout_d01_2005-08-28_00:00:00","r") 
  ter = wrf_user_getvar(a,"HGT",0) ; Get terrain height for time 0 
  wks = gsn_open_wks("png","test") ; Create a plot workstation 
  opts = True ; Set some Basic Plot options 
  opts@MainTitle = "GEOGRID FIELDS" 
  res = opts ; Use basic options for this field 
  res@cnFillOn = True ; Create a color fill plot 
  contour = wrf_contour(a,wks,ter,res) ; contour alone has no display 
  pltres = True ; Set plot options 
  mpres = True ; Set map options 
  mpres@mpGeophysicalLineColor = "Black" ; Overwrite basic map settings 
  mpres@mpGridLineColor = "Black" 
  mpres@mpLimbLineColor = "Black" 
  mpres@mpNationalLineColor = "Black" 
  mpres@mpPerimLineColor = "Black" 
  mpres@mpUSStateLineColor = "Black" 
  plot = wrf_map_overlays(a,wks,(/contour/),pltres,mpres) ; Plot the data over a map background 
end</code></pre>
    </li>
    <li>
        <p>Run the wrf_test.ncl file using ncl.</p>
        <pre><code>conda activate ncl_stable
ncl wrf_test.ncl</code></pre>
        <blockquote>
            <p><strong>Note:</strong> After successful execution, a test.png file will be generated in the current folder.</p>
        </blockquote>
    </li>
</ol>

<h3>Step 8: View Visualization Results</h3>

<p>This document uses the method of attaching an EIP to the compute node to download the png image file to local machine for viewing.</p>

<ol>
    <li>Find the compute node instance in the EHPC console.</li>
    <li>Create an Elastic IP (EIP) and bind it to the compute instance.</li>
    <li>Transfer the image to local machine and view it.</li>
    <pre><code>scp root@Public_IP:/home/wrftest/WRFV3/run/test.png ./</code></pre>
</ol>
