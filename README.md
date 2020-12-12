# ssimulacra-binaries

x64 Window binaries for Cloudinary's [ssimulacra](https://github.com/cloudinary/ssimulacra)

---

**If you would like to compile them yourself, here's how I did it:**

1. Install Visual Studio 2019

   - Choose "Desktop development with C++" in wizard

2. Create a new C++ console application project
3. Copy [ssimulacra.cpp](https://github.com/cloudinary/ssimulacra/blob/master/ssimulacra.cpp) into your Source Files folder.
4. Clone [vcpkg](https://github.com/Microsoft/vcpkg) (Reference: https://docs.microsoft.com/en-us/cpp/build/vcpkg?view=msvc-160)
5. Run `bootstrap-vcpkg.bat`
6. Open console in your vcpkg directory and run `vcpkg install opencv2:x64-windows`
7. Wait
8. Run `vcpkg integrate install`
9. Restart Visual Studio
10. It should no longer complain it can't find opencv2 and the squigly lines should now be gone except for 1 line
11. Comment out `inline void rgb2lab(Vec3f &p) __attribute__ ((hot));`

    - It's just a flag for g++ to optimise this function more aggresively

12. Build your project and it should build without errors.

13. Finally, choose your Configuration (Debug, Release) and Platfom (x86, x64), build it and grab your production dll and exe files
14. (optional) Delete your `downloads` and `buildtrees` folders in vcpkg directory to save space
