# 2. BioHPC

**BioHPC** is the high-performance computing group at UT Southwestern. They offer a range of computational resources, workshops, and cloud storage options designed for research labs on campus. Below is a quick guide to get you started with BioHPC.

For detailed documentation, visit the [BioHPC Portal](https://portal.biohpc.swmed.edu/content/).

---

## 2.1 Getting Access

To obtain access to BioHPC:

1. **Register for an account** on the registration page [BioHPC Registration](https://portal.biohpc.swmed.edu/intranet/accounts/register/).
2. **Attend the orientation workshop**:
   - Held on the first Wednesday of every month.
   - Sign up by emailing the support team at [biohpc-help@utsouthwestern.edu](mailto:biohpc-help@utsouthwestern.edu).
3. After completing the workshop, your account will be activated, granting you access to BioHPC resources.

---

## 2.2 Directory Organization

Once your account is activated, you will have access to the following directories:

### **1. `/home2`**
- Your personal home directory: `/home2/[your UT Southwestern ID]`.
- Storage Limit: **50 GB**.
- Use it primarily for backing up your code.

### **2. `/work`**
- Your work directory for analysis and results: `/work/[your ID]`.
- Storage Capacity: **5 TB**.
- Store larger datasets, analysis outputs, and results here.

### **3. `/project`**
- Shared lab data directory: `/project/TIBIR/Lega_lab/shared/lega_ansir/`.
- Key folders in the project directory:
  - **`shared_code`**: Contains essential resources like the EEG toolbox, data processing scripts, and tutorials.
  - **`subjFiles`**: Houses subject-specific data, organized as follows:
    - `behavioral`: Behavioral task data in event structures.
    - `docs`: Miscellaneous documentation (e.g., electrode labels).
    - `eeg.noreref`: Raw EEG data.
    - `eeg.reref`: Rereferenced EEG data using an average scheme.
    - `freesurfer`: CT and MRI files.
    - `raw`: Original EEG files from clinical systems.
    - `tal`: Electrode localization data in Talairach coordinates.

**Tip**: Use `/work` for active projects and `/home2` for backups. Keep data organized to ensure efficient storage usage.

---

## 2.3 Working on the Cloud

### **Web Visualization**
1. **Download TurboVNC**: [TurboVNC Website](https://www.turbovnc.org/).
2. **Start Web Visualization** on the BioHPC website to obtain:
   - Node address
   - Password
3. Launch TurboVNC and connect using the provided details. A Linux desktop will appear, preloaded with tools like Matlab, Python, and R.

**Starting Matlab**:
- Open terminal.
- Check available versions: `module avail matlab`.
- Load your preferred version: `module load matlab/[version]`.
- Start Matlab: `matlab`.

---

### **Mounting Cloud Directories**

Access cloud directories directly on your local machine:

1. **For macOS**:
   - Go to `Finder -> Go -> Connect to Server`.
   - Enter the server address:
     - `/home2`: `smb://lamella.biohpc.swmed.edu/<username>`
     - `/project`: `smb://lamella.biohpc.swmed.edu/project`
     - `/work`: `smb://lamella.biohpc.swmed.edu/work`
   - Log in using your BioHPC credentials.

This method is useful for transferring small files and performing offline analysis.

---

## 2.4 Running Parallel Jobs

BioHPC supports parallel computing for faster task execution.

### **Steps to Set Up Parallel Jobs:**
1. Use the provided code in `/shared_code/tutorial/parallel_jobs`:
   - **`lockfile_template.m`**: Template for organizing parallel scripts.
2. Organize your script:
   - Use a main `for` loop for parallel processing.
   - Include a `try/catch` block for independent iteration processing.
   - Create "lock," "done," and "error" files to monitor progress.
3. Use the shell scripts:
   - Copy `srunScript.sh` and `matlabWrapper.sh` to your `/work` directory.
   - Modify as needed for your use case.
4. Submit the job:
   - Use the Nucleus Web Terminal:
     ```bash
     sbatch /work/[location_of_srunScript.sh]
     ```

For more details, refer to the [BioHPC job submission tutorial](https://portal.biohpc.swmed.edu/intranet/sbatch/#/script).

---

## 2.5 Access from Off-Campus

To access BioHPC remotely:

1. Download and install **GlobalProtect** ([UTSW Instructions](https://www.utsouthwestern.edu/about-us/administrative-offices/information-resources/working-remotely.html)). Download link is on Step 4 of the UTSW page. 
2. Configure the VPN:
   - Server Name: `myutswvpn.swmed.edu`.
   - Log in using your UT Southwestern credentials.
   - Authenticate using Duo Mobile for the secondary password.
3. Once connected, you can use BioHPC as if on campus.

---

For additional help, email the support team at [biohpc-help@utsouthwestern.edu](mailto:biohpc-help@utsouthwestern.edu). Make the most of BioHPC’s resources to enhance your research work!
