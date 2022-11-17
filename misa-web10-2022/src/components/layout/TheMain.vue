<template>
    <div class="ct__maincontent">
                    <div class="maincontent--header">
                            <div class="text-title">Nhân viên</div>
                            <button id="btnAdd" class="btn-add">Thêm mới nhân viên</button>                      
                    </div>  
                        
                    <div class="table--tbr">
                        <div class="table--tbr-head">
                            <div class="tb-head-tool">
                                <div class="input--icons">
                                    <input id="search" class="inpt" type="text" value placeholder="Tìm theo mã, tên nhân viên">
                                    <div class="icon-tagl icon-sear "></div>
                                </div>
                                <div id="btnRefresh" class="icon-center icon-refresh tooltip">
                                    <span>Lấy lại dữ liệu</span>
                                </div>
                            </div>
                        </div>    
                        <div class="table">
                            <table class="text-tb-main" id="tbEmployee">
                                <col>
                                <col>
                                <col>
                                <thead class="text-tb-head">
                                    <tr>
                                        <th propValue="checkbox" class="tbl-center">
                                            <div class="checkboxContainer">
                                                <div class="checkbox-tbl"></div>
                                            </div>
                                        </th>
                                        <th propValue="EmployeeCode" format="text-left" class="text-left">Mã nhân viên</th>
                                        <th propValue="EmployeeName" format="emplName" class="text-left">Họ và tên</th>
                                        <th propValue="Gender" format="gender" class="text-left">Giới tính</th>
                                        <th propValue="DateOfBirth" format="date" class="text-center">Ngày sinh</th>
                                        <th propValue="IdentityNumber" format="text-left" class="text-left">Số CMND</th>
                                        <th propValue="IdentityDate" format="date" class="text-center">Ngày cấp</th>
                                        <th propValue="IdentityPlace" format="text-left" class="text-left">Nơi cấp</th>
                                        <th propValue="PositionName" format="text-left" class="text-left">Chức danh</th>
                                        <th propValue="PhoneNumber" format="text-right" class="text-right">Điện thoại</th>
                                        <th propValue="DepartmentName" format="text-left" class="text-left">Phòng ban</th>
                                        <th propValue="Email" format="text-left" class="text-left">Email</th>
                                        <th propValue="BankAccountNumber" format="text-right" class="text-right">Số tài khoản</th>
                                        <th propValue="Salary" format="money" class="text-right">Mức lương cơ bản</th>
                                        <th propValue="control">Chức năng</th>
                                    </tr>
                                </thead>
                                <tbody v-for="(item,index) in employees" :key="index">
                                    <tr>
                                        <td :class="tbl-center" :propValue="checkbox">
                                            <div class="checkboxContainer">
                                                <div class="checkbox-tbl"></div>
                                            </div>
                                        </td>
                                        <td class="text-left">{{item.EmployeeCode}}</td>
                                        <td class="text-left">{{item.EmployeeName}}</td>
                                        <td class="text-left">{{item.Gender}}</td>
                                        <td class="text-center">format {{item.DateOfBirth}}</td>
                                        <td class="text-left">{{item.IdentityNumber}}</td>
                                        <td class="text-center">{{item.IdentityDate}}</td>
                                        <td class="text-left">{{item.IdentityPlace}}</td>
                                        <td class="text-left">{{item.PositionName}}</td>
                                        <td class="text-right">{{item.PhoneNumber}}</td>
                                        <td class="text-left">{{item.DepartmentName}}</td>
                                        <td class="text-left">{{item.Email}}</td>
                                        <td class="text-left">{{item.BankAccountNumber}}</td>
                                        <td class="text-right">{{item.Salary}}</td>
                                        <td class="control">
                                            <div id="btnDel" class="text-control">Sửa</div>
                                            <div class="control-icon icon-control"></div>
                                        </td>
                                    </tr>    
                                </tbody>
                            </table>
                        </div>     
                    </div>
                    <div class="maincontent--paging">
                        <div class="paging">
                            <div class="text-paging">Tổng số:  bản ghi</div>
                            <div class="fliter">
                                <div class="dropdown-filter">
                                    <div text-filter>Số bản ghi/trang:</div>
                                    <div class="icon-filter-dropdown icon-arrow-right"></div>
                                </div>
                                <div class="text-filter">bản ghi</div>
                                <div class="icon-center icon-arrow-left"></div>
                                <div class="icon-center icon-arrow-right"></div>
                            </div>
                        </div>
                    </div>                       
                </div>
</template>

<script>
    import axios from 'axios'
    
    export default{
        name: "TheMain",
        created() {
          /**
           * Lấy danh sách nhân viên từ API
           */  
          const getAllEmployee = async()=>{
            try {
                const res = await axios.get('https://amis.manhnv.net/api/v1/employees')
                this.employees = res.data
                this.cout = res
            } catch (error) {
                console.log(error);
            }
          }
            getAllEmployee()

          /**
         * Hàm định dạng date cho ô nhập dữ liệu khách hàng
         * @param {any} date 
         * @returns 
         */
        function formatDateForDlg(date) {
            let dateValue = ""
            let month = ""
            try {
                if(this.date) {
                    date = new Date(date);
                    //Ngay
                    if(date.getDate() < 10)
                        dateValue = String("0" + date.getDate());
                    else 
                        dateValue = String(date.getDate());
                        
                    //Thang
                    if (date.getMonth() < 10)
                        month = String("0" + (date.getMonth() + 1));//Thang lay tu 0
                    else 
                        month = String(date.getMonth() + 1);//Thang lay tu 0
                    
                    //Nam
                    let year = date.getFullYear();
                    return `${dateValue}/${month}/${year}`; 
                }else{
                    return "";
                }
            } catch (error) {
                console.log(error)
            }
        }
        formatDateForDlg()
        },
        data() {
            return {
                date:"",
                cout:0,
                employees:[]
            }
        },

    }
</script>
<style scoped>

</style>