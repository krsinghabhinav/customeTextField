# customeTextField

import 'package:flutter/material.dart';
import 'package:get/get.dart';

class loginCustomTextFieldWidget extends StatelessWidget {
  final String hintText;
  final Color color;
  final IconData prefixIcon;
  final IconData? suffixIcon;
  final VoidCallback? onSuffixIconTap;
  final ValueChanged<String>? onchange;
  final TextEditingController controller;
  final TextInputType keyboardType;
  final bool obscureText;
  final String? Function(String?)? validator; // Added validator

  const loginCustomTextFieldWidget(
      {Key? key,
      required this.hintText,
      required this.prefixIcon,
      this.suffixIcon,
      this.onSuffixIconTap,
      required this.controller,
      this.keyboardType = TextInputType.text,
      this.obscureText = false,
      this.validator,
      this.color = Colors.white,
      this.onchange})
      : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.symmetric(horizontal: 30),
      child: Container(
        height: Get.height * 0.07,
        decoration: BoxDecoration(
          color: color,
          borderRadius: BorderRadius.circular(20),
        ),
        child: TextFormField(
          onChanged: onchange,
          controller: controller,
          keyboardType: keyboardType,
          obscureText: obscureText,
          style: TextStyle(color: Colors.white),
          decoration: InputDecoration(
            border: InputBorder.none,
            hintText: hintText,
            hintStyle: TextStyle(color: Colors.white),
            prefixIcon: Icon(prefixIcon, color: Colors.white),
            suffixIcon: suffixIcon != null
                ? GestureDetector(
                    onTap: onSuffixIconTap,
                    child: Icon(suffixIcon, color: Colors.white),
                  )
                : null,
            contentPadding: const EdgeInsets.symmetric(vertical: 15),
          ),
          validator: validator,
        ),
      ),
    );
  }
}
