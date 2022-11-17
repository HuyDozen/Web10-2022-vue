<template>
  <!-- <div class="container">
    <the-sibar></the-sibar>
    <div class="ct__item">
      <the-header></the-header>
      <the-main></the-main>
      
    </div>   
  </div> -->
    <div class="container">   
        <the-sibar></the-sibar>
        <div class="ct__item">
            <the-header></the-header>       
            <the-main></the-main>
        </div>
    </div>

    <!-- dialog thong tin nhan vien -->
    <div id="dlgEmployeeInfor" class="dialog" hidden>
        <div class="dialog__delete">
            <div class="dlg__del-header">
                <div class="dlg__del-header--title">
                    <div class="title-dialog"> Thông tin nhân viên</div>
                    <div class="check-title">
                        <div class="checkbox"></div>
                        <div>Là khách hàng</div>
                    </div> 
                    <div class="check-title">
                        <div class="checkbox"></div>
                        <div>Là nhà cung cấp</div>
                    </div> 
                    
                </div>
                <div class="dlg-header-icon">
                    <div class="icon-center icon-question tooltip">
                        <div class="arrow-up"></div>
                        <div class="tooltipDlg" >Giúp (F1)</div>
                    </div>
                    <div class="btnClose icon-center icon-close tooltip">
                        <div class="arrow-up"></div>
                        <div class="tooltipDlg">Đóng (ESC)</div>
                    </div>
                </div>
            </div>
            <div class="dlg-infor-content">
                <div class="dlg-content-row1">
                    <div class="dlg-row1-col1">
                        <div class="dlg-row-content">
                            <div class="m-col">
                                <div class="text-dlg">Mã <span class="span-red">*</span></div>
                                <div class="input-EmplCode" >
                                    <input propValue="EmployeeCode" id="txtEmployeeCode" note="Mã nhân viên"  class="input-dlg input-dlg-id" type="text" required>
                                    <span hidden>Mã không được để trống.</span>
                                </div>
                                
                            </div>
                            <div class="m-col">
                                <div class="text-dlg">Tên <span class="span-red">*</span></div>
                                <div class="input-EmplName" >
                                    <input propValue="EmployeeName" id="txtEmployeeName" note="Tên nhân viên" class="input-dlg input-dlg-name" type="text" required>
                                    <span hidden>Tên không được để trống.</span>
                                </div>
                               
                            </div>
                        </div>
                        <div class="dlg-row-content">
                            <div class="m-col">
                                <div class="text-dlg">Đơn vị <span class="span-red">*</span></div>
                                <div class="input-EmplPosition" >
                                    <input propValue="DepartmentId" id="txtEmployeeDepartment" note="Đơn vị" class="input-dlg input-dlg-full-width" type="text" required>
                                    <span hidden>Đơn vị không được để trống.</span>
                                </div>
                                
                            </div>
                        </div>
                        <div class="dlg-row-content">
                            <div class="m-col">
                                <div class="text-dlg">Chức danh </div>
                                <input id="txtEmployeePosition" class="input-dlg input-dlg-full-width" type="text" value="">
                            </div>
                        </div>
                    </div>
                    <div class="dlg-row1-col2">
                        <div class="dlg-row-content">
                            <div class="m-col">
                                <div class="text-dlg">Ngày sinh</div>
                                <input type="date" name="dateofbirth" id="dateEmployee">
                            </div>
                            <div class="m-col">
                                <div class="text-dlg">Giới tính</div>
                                <div class="row-radio">
                                    <label class="radio-container">Nam
                                      <input type="radio" checked="checked" name="radio">
                                      <span class="checkmark"></span>
                                    </label>
                                    <label class="radio-container">Nữ
                                      <input type="radio" name="radio">
                                      <span class="checkmark"></span>
                                    </label>
                                    <label class="radio-container">Khác
                                      <input type="radio" name="radio">
                                      <span class="checkmark"></span>
                                    </label>
                                  </div>
                            </div>
                        </div>
                        <div class="dlg-row-content">
                            <div class="m-col">
                                <div class="text-dlg tooltip">Số CMND
                                    <span>Số chứng minh nhân dân</span>
                                </div>
                                <input id="identifyNumEmployee" class="input-dlg input-dlg-identify" type="text" value="">
                                
                            </div>
                            <div class="m-col">
                                <div id="identifyDate" class="text-dlg">Ngày cấp</div>
                                <input class="" type="date" name="dateofbirth" id="dateIdentify">
                            </div>
                        </div>
                        <div class="dlg-row-content">
                            <div class="m-col">
                                <div class="text-dlg">Nơi cấp</div>
                                <input id="identifyPlace" class="input-dlg input-dlg-full-width" type="text" value="">
                            </div>
                        </div>
                    </div>
                </div>
                <div class="dlg-content-row3">
                    <div class="m-col">
                        <div class="text-dlg">Địa chỉ</div>
                        <input id="addressEpl" class="input-dlg input-dlg-address" type="text" value="">
                    </div>
                    <div class="dlg-row-content">
                        <div class="m-col">
                            <div class="text-dlg">ĐT di động</div>
                            <div class="input-EmlPhoneNumber">
                                <input id="phoneNumberEpl" class="input-dlg input-dlg-phone-mail" type="text">
                                <span hidden>Số điện thoại phải có 10 chữ số.</span>
                            </div>
                        </div>
                        <div class="m-col">
                            <div class="text-dlg">ĐT cố định</div>
                            <div class="input-EmplLandlinePhone">
                                <input id="landlinePhoneEpl" class="input-dlg input-dlg-phone-mail" type="text">
                                <span hidden>Điện thoại cố định nhập chưa đúng định dạng</span>
                            </div>
                        </div>
                        <div class="m-col">
                            <div class="text-dlg">Email</div>
                            <div class="input-EmplEmail">
                                <input id="txtEmail" class="input-dlg input-dlg-phone-mail" type="email">
                                <span hidden>Email nhập chưa đúng định dạng.</span>
                            </div>
                        </div>
                    </div>
                    <div class="dlg-row-content">
                        <div class="m-col">
                            <div class="text-dlg">Tài khoản ngân hàng</div>
                            <input id="accountBank" class="input-dlg input-dlg-phone-mail" type="text" value="">
                        </div>
                        <div class="m-col">
                            <div class="text-dlg">Tên ngân hàng</div>
                            <input id="nameBank" class="input-dlg input-dlg-phone-mail" type="text" value="">
                        </div>
                        <div class="m-col">
                            <div class="text-dlg">Chi nhánh</div>
                            <input id="branchBank" class="input-dlg input-dlg-phone-mail" type="text" value="">
                        </div>
                    </div>
                </div>
                <div class="dlg-content-row4">                
                    <button class="btnClose btn btn-cancel ">Huỷ</button>
                    <div class="btn-dlg-func">
                        <button id="btnSave"  class="btn btn-save">Cất</button>
                        <button id="btnSave-Add" class="btn btn-save-add">Cất và thêm</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- dialog cảnh báo-->
    <div id="dlgWarning" class="dialog" hidden>
        <div class="mbox-form">
            <div class="mbox-content">
                <div class="mbox-title">
                    <div class="mbox-row-content">
                        <div class="icon-mbox icon-warning"></div>
                        <div class="text-warning">Tên không được để trống</div>
                    </div>            
                </div>
                <div class="mbox-line"></div>
                <div class="mbox-btn">
                    <button class="btnClose btn btn-save-add">Đóng</button>
                </div>      
            </div>
        </div>
    </div>

    <div id="dlg-loading" class="dialog" hidden>
        <div class="loading">
            <iframe src="/assets/loading.svg" frameborder="0"></iframe>
        </div>
    </div>
  
</template>

<script>

import TheSibar from './components/layout/TheSibar.vue'
import TheMain from './components/layout/TheMain.vue'
import TheHeader from './components/layout/TheHeader.vue'
// import axios from 'axios'
export default {
  name: 'App',
  components: {
    TheSibar,
    TheMain,
    TheHeader
  },
  

  data() {
    return {
        
    }
  },
}
</script>

<style scoped>
/* @import url(./css/layout/sidebar.css); */
@import url(./css/main/style.css);

</style>
